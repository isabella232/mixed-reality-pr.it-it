---
title: HoloLens (prima generazione) Condivisione 240 - Più HoloLens dispositivi
description: Seguire questa procedura dettagliata di scrittura del codice usando Unity, Visual Studio e HoloLens informazioni dettagliate sulla condivisione di ologrammi.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, condivisione, rete, academy, esercitazione, HoloLens, Mixed Reality Academy, unity, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale, Windows 10
ms.openlocfilehash: 1714c9cf1b64953ff319eefb8633b1891568d5a50f2ed778e6e890d3149d3908
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208701"
---
# <a name="hololens-1st-gen-sharing-240-multiple-hololens-devices"></a>HoloLens (prima generazione) Condivisione 240: più HoloLens dispositivi

>[!IMPORTANT]
>Le esercitazioni di Mixed Reality Academy sono state progettate per HoloLens (prima generazione), Unity 2017 e visori VR immersive di Realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi. Queste esercitazioni non **_verranno_** aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2 e potrebbero non essere compatibili con le versioni più recenti di Unity.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md).

Ologrammi la presenza nel mondo rimanendo al suo posto mentre ci si sposta nello spazio. HoloLens mantiene gli ologrammi sul posto usando vari sistemi di [coordinate](../../../design/coordinate-systems.md) per tenere traccia della posizione e dell'orientamento degli oggetti. Quando si condividono questi sistemi di coordinate tra dispositivi, è possibile creare un'esperienza condivisa che consente di partecipare a un mondo olografico condiviso.

In questa esercitazione si apprenderà come:

* Configurare una rete per un'esperienza condivisa.
* Condividere ologrammi tra HoloLens dispositivi.
* Scopri altre persone nel nostro mondo olografico condiviso.
* Creare un'esperienza interattiva condivisa in cui è possibile scegliere come destinazione altri lettori e avviare i proiettori.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Condivisione MR 240: Più dispositivi HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un Windows 10 pc configurato con gli strumenti [corretti installati con](../../../develop/install-the-tools.md) l'accesso a Internet.
* Almeno due dispositivi HoloLens [configurati per lo sviluppo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) richiesti dal progetto. Richiede Unity 2017.2 o versione successiva.
  * Se è ancora necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Se è ancora necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Se è ancora necessario il supporto di Unity 5.4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facilmente raggiungibile. Mantenere il nome della cartella **SharedHolograms.**

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è disponibile [in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capitolo 1 - Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

In questo capitolo si configura il primo progetto Unity e si esegue il processo di compilazione e distribuzione.

### <a name="objectives"></a>Obiettivi

* Configurare Unity per sviluppare app olografiche.
* Vedere l'ologramma.

### <a name="instructions"></a>Istruzioni

* Riavviare Unity.
* Selezionare **Open** (Apri).
* Immettere location come **cartella SharedHolograms** non gerarchicata in precedenza.
* Selezionare **Project nome e** fare clic su Seleziona **cartella.**
* In **Gerarchia fare** clic con il pulsante destro **del mouse sulla fotocamera principale** e scegliere **Elimina.**
* Nella cartella **HoloToolkit-Sharing-240/Prefabs/Camera** trovare il prefab **Della** fotocamera principale.
* Trascinare e rilasciare **main camera (Fotocamera** principale) in **Hierarchy (Gerarchia).**
* In **Hierarchy (Gerarchia)** fare clic **su Create** and **Create Empty (Crea e crea vuoto).**
* Fare clic con il pulsante destro del **mouse sul nuovo GameObject** e **scegliere Rinomina.**
* Rinominare GameObject in **HologramCollection.**
* Selezionare **l'oggetto HologramCollection** nella **gerarchia**.
* In **Inspector (Controllo)** impostare **la posizione della** trasformazione su: **X: 0, Y: -0.25, Z: 2**.
* Nella cartella **Ologrammi** nel pannello Project **trovare** l'asset **EnergyHub.**
* Trascinare e **rilasciare l'oggetto EnergyHub** **dal Project alla** gerarchia come elemento figlio di **HologramCollection.** 
* Selezionare **File > Salva scena con nome...**
* Assegnare alla scena **il nome SharedHolograms e fare** clic su **Salva.**
* Premere il **pulsante Play** (Riproduci) in Unity per visualizzare in anteprima gli ologrammi.
* Premere **Riproduci** una seconda volta per arrestare la modalità di anteprima.

**Esportare il progetto da Unity in Visual Studio**

* In Unity selezionare **File > Build Impostazioni**.
* Fare **clic su Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena.
* Selezionare **Universal Windows Platform nell'elenco** Piattaforma **e** fare clic su **Cambia piattaforma.**
* Impostare **SDK** su **Universal 10**.
* Impostare **Dispositivo di destinazione** su **HoloLens** e Tipo di **compilazione UWP** su **D3D.**
* Controllare **i progetti C# di Unity.**
* Fare clic su **Compila**.
* Nella finestra di Esplora file visualizzata creare una **nuova cartella** denominata "App".
* Fare clic sulla **cartella App.**
* Fare clic **su Seleziona cartella**.
* Al termine dell'operazione, verrà Esplora file finestra di dialogo.
* Aprire la **cartella App.**
* Aprire **SharedHolograms.sln** per avviare Visual Studio.
* Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Release** e da ARM a **X86.**
* Fare clic sulla freccia a discesa accanto a Computer locale e selezionare **Dispositivo remoto.**
    * Impostare **Indirizzo** sul nome o sull'indirizzo IP del HoloLens. Se non si conosce l'indirizzo IP del dispositivo, cercare in Opzioni avanzate di **Impostazioni > Rete & Internet >** o chiedere Cortana "Hey Cortana, Qual è **l'indirizzo IP?"**
    * Lasciare **l'opzione Modalità di** autenticazione impostata su **Universale.**
    * Fare clic **su Seleziona**
* Fare **clic su Debug > Avvia senza eseguire** debug o premere **CTRL+F5.** Se è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarlo a Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
* Posizionare il HoloLens e trovare l'ologramma di EnergyHub.

## <a name="chapter-2---interaction"></a>Capitolo 2 - Interazione

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

In questo capitolo si interagirà con gli ologrammi. Prima di tutto, si aggiungerà un cursore per visualizzare lo [sguardo fisso.](../../../design/gaze-and-commit.md) Si aggiungeranno quindi i [movimenti e](../../../design/gaze-and-commit.md#composite-gestures) si userà la mano per posizionare gli ologrammi nello spazio.

### <a name="objectives"></a>Obiettivi

* Usare l'input dello sguardo fisso per controllare un cursore.
* Usare l'input del movimento per interagire con gli ologrammi.

### <a name="instructions"></a>Istruzioni

**Sguardo fisso**

* Nel pannello **Hierarchy (Gerarchia)** seleziona **l'oggetto HologramCollection.**
* Nel pannello **Inspector (Controllo)** fai clic **sul pulsante Add Component (Aggiungi** componente).
* Nel menu digitare nella casella di ricerca **Gestione sguardo fisso**. Selezionare il risultato della ricerca.
* Nella cartella **HoloToolkit-Sharing-240\Prefabs\Input** trovare l'asset **Cursore.**
* Trascinare e rilasciare **l'asset Cursore** in **Hierarchy**.

**Movimento**

* Nel pannello **Hierarchy (Gerarchia)** seleziona **l'oggetto HologramCollection.**
* Fare **clic su Aggiungi** componente e digitare Gestione **movimenti** nel campo di ricerca. Selezionare il risultato della ricerca.
* Nel pannello **Gerarchia** espandere **HologramCollection**.
* Selezionare **l'oggetto EnergyHub** figlio.
* Nel pannello **Controllo fare** clic sul **pulsante Aggiungi** componente.
* Nel menu digitare nella casella di ricerca **Hologram Placement**. Selezionare il risultato della ricerca.
* Salvare la scena selezionando File > **Salva scena**.

**Distribuire e usufruire**

* Compilare e distribuire nel HoloLens, usando le istruzioni del capitolo precedente.
* Quando l'app viene avviata nel HoloLens, spostare la testa e notare come EnergyHub segue lo sguardo.
* Si noti come il cursore viene visualizzato quando si guarda l'ologramma e si cambia in una luce punto quando non si guarda un ologramma.
* Eseguire un tocco d'aria per posizionare l'ologramma. A questo punto nel progetto, è possibile inserire l'ologramma una sola volta (ridistribuire per riprovare).

## <a name="chapter-3---shared-coordinates"></a>Capitolo 3 - Coordinate condivise

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

È divertente vedere e interagire con gli ologrammi, ma si va oltre. Verrà impostata la prima esperienza condivisa: un ologramma che tutti possono vedere insieme.

### <a name="objectives"></a>Obiettivi

* Configurare una rete per un'esperienza condivisa.
* Stabilire un punto di riferimento comune.
* Condividere sistemi di coordinate tra dispositivi.
* Tutti vedono lo stesso ologramma.

>[!NOTE]
>Le **funzionalità InternetClientServer** **e PrivateNetworkClientServer** devono essere dichiarate perché un'app si connetta al server di condivisione. Questa operazione viene eseguita già in Ologrammi 240, ma tenere presente questo problema per i propri progetti.

>1. Nell'editor di Unity passare alle impostazioni del lettore passando a "Modifica > Project Impostazioni > lettore"
>2. Fare clic sulla scheda "Windows Store"
>3. Nella sezione "Funzionalità Impostazioni > pubblicazione" controllare la **funzionalità InternetClientServer** e la **funzionalità PrivateNetworkClientServer**

### <a name="instructions"></a>Istruzioni

* Nel pannello **Project passare** alla **cartella HoloToolkit-Sharing-240\Prefabs\Sharing.**
* Trascinare e rilasciare **il** prefab Condivisione nel **pannello Gerarchia**.

È quindi necessario avviare il servizio di condivisione. Solo **un PC** nell'esperienza condivisa deve eseguire questo passaggio.

* In Unity, nel menu in alto, selezionare **il menu HoloToolkit-Sharing-240.**
* Selezionare **l'elemento Avvia servizio** di condivisione nell'elenco a discesa.
* Selezionare **l'opzione Rete** privata e fare clic **su Consenti accesso** quando viene visualizzata la richiesta del firewall.
* Prendere nota dell'indirizzo IPv4 visualizzato nella finestra della console del servizio di condivisione. Si tratta dello stesso IP del computer in cui viene eseguito il servizio.

Seguire le altre istruzioni in tutti **i PC** che verranno uniti all'esperienza condivisa.

* In **Gerarchia** selezionare **l'oggetto** Condivisione.
* In **Inspector**(Controllo) nel componente **Sharing Stage** (Fase di condivisione) modificare **l'indirizzo** del server da "localhost" all'indirizzo IPv4 del computer che esegue SharingService.exe.
* Nella **gerarchia** selezionare **l'oggetto HologramCollection.**
* In Inspector **(Controllo)** fare clic **sul pulsante Add Component (Aggiungi** componente).
* Nella casella di ricerca digitare **Import Export Anchor Manager**. Selezionare il risultato della ricerca.
* Nel pannello **Project passare** alla **cartella** Script.
* Fare doppio clic nello script **HologramPlacement** per aprirlo in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* In Unity selezionare **HologramCollection** nel pannello **Gerarchia**.
* Nel pannello **Controllo fare** clic sul **pulsante Aggiungi** componente.
* Nel menu digitare nella casella di ricerca **App State Manager**. Selezionare il risultato della ricerca.

**Distribuire e usufruire**

* Compilare il progetto per i HoloLens mobili.
* Designare una HoloLens in cui eseguire la distribuzione. È necessario attendere che l'ancoraggio venga caricato nel servizio prima di poter posizionare EnergyHub (l'operazione può richiedere circa 30-60 secondi). Fino al termine del caricamento, i movimenti di tocco verranno ignorati.
* Dopo aver inserito EnergyHub, la relativa posizione verrà caricata nel servizio ed è quindi possibile distribuirlo in tutti gli altri HoloLens dispositivi.
* Quando un nuovo HoloLens per la prima volta si unisce alla sessione, la posizione di EnergyHub potrebbe non essere corretta in tale dispositivo. Tuttavia, non appena i percorsi di ancoraggio e EnergyHub sono stati scaricati dal servizio, EnergyHub dovrebbe passare alla nuova posizione condivisa. Se questa operazione non avviene entro circa 30-60 secondi, andare a dove si trova il HoloLens originale quando si imposta l'ancoraggio per raccogliere altri indizi sull'ambiente. Se il percorso non si blocca ancora, ridistribuire nel dispositivo.
* Quando i dispositivi sono tutti pronti ed eseguono l'app, cercare EnergyHub. È possibile concordare tutti sulla posizione dell'ologramma e sulla direzione in cui si trova il testo?

## <a name="chapter-4---discovery"></a>Capitolo 4 - Individuazione

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Tutti possono ora vedere lo stesso ologramma. Ora vediamo tutti gli altri utenti connessi al nostro mondo olografico condiviso. In questo capitolo verrà presa la posizione head e la rotazione di tutti gli altri dispositivi HoloLens nella stessa sessione di condivisione.

### <a name="objectives"></a>Obiettivi

* Scoprirsi a vicenda nell'esperienza condivisa.
* Scegliere e condividere un avatar del giocatore.
* Collegare l'avatar del giocatore accanto alle teste di tutti.

### <a name="instructions"></a>Istruzioni

* Nel pannello **Project passare** alla **cartella** Ologrammi.
* Trascinare e rilasciare **PlayerAvatarStore** in **Hierarchy**.
* Nel pannello **Project passare** alla **cartella** Script.
* Fare doppio clic su **AvatarSelector** script per aprirlo in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* Nella **gerarchia** selezionare **l'oggetto HologramCollection.**
* Nel controllo **fare** clic **su Aggiungi componente**.
* Nella casella di ricerca digitare **Local Player Manager**. Selezionare il risultato della ricerca.
* Nella **gerarchia** selezionare **l'oggetto HologramCollection.**
* Nel controllo **fare** clic **su Aggiungi componente**.
* Nella casella di ricerca digitare **Remote Player Manager**. Selezionare il risultato della ricerca.
* Aprire lo script **HologramPlacement** in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Aprire lo script **AppStateManager** in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Distribuire e usufruire**

* Compilare e distribuire il progetto nei dispositivi HoloLens dispositivo.
* Quando si ascolta un suono di ping, trovare il menu di selezione dell'avatar e selezionare un avatar con il movimento di tocco dell'aria.
* Se non si sta esaminando alcun ologramma, la luce del punto intorno al cursore assume un colore diverso quando il HoloLens comunica con il servizio: inizializzazione (viola scuro), download dell'ancoraggio (verde), importazione/esportazione dei dati sulla posizione (giallo), caricamento dell'ancoraggio (blu). Se la luce del punto intorno al cursore è il colore predefinito (viola chiaro), si è pronti per interagire con altri giocatori nella sessione.
* Guarda altre persone connesse al tuo spazio: sopra la loro scapola ci sarà un robot olografico che simula i movimenti della testa.

## <a name="chapter-5---placement"></a>Capitolo 5 - Posizionamento

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

In questo capitolo si farà in modo che l'ancoraggio possa essere posizionato su superfici reali. Verranno usate coordinate condivise per posizionare l'ancoraggio nel punto intermedio tra tutti gli utenti connessi all'esperienza condivisa.

### <a name="objectives"></a>Obiettivi

* Posizionare gli ologrammi sulla mesh di mapping spaziale in base alla posizione della testa dei giocatori.

### <a name="instructions"></a>Istruzioni

* Nel pannello **Project passare** alla **cartella** Ologrammi.
* Trascinare e rilasciare il prefab **CustomSpatialMapping** in **Hierarchy**.
* Nel pannello **Project passare** alla **cartella** Script.
* Fare doppio clic nello script **AppStateManager** per aprirlo in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* Nel pannello **Project passare** alla **cartella** Script.
* Fare doppio clic nello script **HologramPlacement** per aprirlo in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Distribuire e usufruire**

* Compilare e distribuire il progetto nei dispositivi HoloLens dispositivo.
* Quando l'app è pronta, tenere un cerchio e notare come Viene visualizzato EnergyHub al centro di tutti gli utenti.
* Toccare per posizionare EnergyHub.
* Provare il comando vocale "Reimposta destinazione" per selezionare il backup di EnergyHub e collaborare come gruppo per spostare l'ologramma in una nuova posizione.

## <a name="chapter-6---real-world-physics"></a>Capitolo 6 - Real-World Fisica

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

In questo capitolo verranno aggiunti ologrammi che rimbalzano sulle superfici reali. Guarda lo spazio riempito con i progetti avviati da te e dai tuoi amici.

### <a name="objectives"></a>Obiettivi

* Avviare i proiettori che rimbalzano sulle superfici reali.
* Condividere i proiettori in modo che altri giocatori possano vederli.

### <a name="instructions"></a>Istruzioni

* Nella **gerarchia** selezionare **l'oggetto HologramCollection.**
* Nel controllo **fare** clic **su Aggiungi componente**.
* Nella casella di ricerca digitare **Projectile Launcher**. Selezionare il risultato della ricerca.

**Distribuire e usufruire**

* Compilare e distribuire nei dispositivi HoloLens dispositivo.
* Quando l'app è in esecuzione su tutti i dispositivi, eseguire un tocco d'aria per avviare il proiettore sulle superfici reali.
* Scopri cosa accade quando il tuo proiettore entra in collisione con l'avatar di un altro giocatore.

## <a name="chapter-7---grand-finale"></a>Capitolo 7 - Gran finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

In questo capitolo si scoprirà un portale che può essere individuato solo con collaborazione.

### <a name="objectives"></a>Obiettivi

* Collaborare per lanciare un numero sufficiente di proiettori sull'ancoraggio per scoprire un portale segreto.

### <a name="instructions"></a>Istruzioni

* Nel pannello **Project passare** alla **cartella** Ologrammi.
* Trascinare e rilasciare l'asset **Underworld** come **figlio di HologramCollection**.
* Con **HologramCollection selezionato,** fare clic **sul pulsante Aggiungi** componente in **Inspector**.
* Nel menu digitare nella casella di ricerca **ExplodeTarget**. Selezionare il risultato della ricerca.
* Con **HologramCollection selezionato,** dalla **gerarchia** trascinare l'oggetto **EnergyHub** nel **campo Target** in **Inspector**.
* Con **HologramCollection selezionato,** dalla **gerarchia** trascinare l'oggetto **Underworld** nel **campo Underworld** in **Inspector**.

**Distribuire e usufruire**

* Compilare e distribuire nei dispositivi HoloLens dispositivo.
* Dopo l'avvio dell'app, collaborare per avviare i proiettori in EnergyHub.
* Quando viene visualizzato il mondo inferocito, lanciare i proiettori ai robot del mondo inferocito (ha colpito un robot tre volte per un divertimento più divertente).