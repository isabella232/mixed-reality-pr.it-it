---
title: HoloLens (prima generazione) Input 210 - Gaze
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi agli sguardi.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gaze, HoloLens, Mixed Reality Academy, unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, Windows 10
ms.openlocfilehash: e0d761c6292502f381618f8efa1bed9d26f0e6fbac8dbdafa8085e0bb41676ce
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220977"
---
# <a name="hololens-1st-gen-input-210-gaze"></a>HoloLens (prima generazione) Input 210: Sguardo fisso

>[!IMPORTANT]
>Le esercitazioni di Mixed Reality Academy sono state progettate con HoloLens (prima generazione), Unity 2017 e Visori immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi. Queste esercitazioni **_non verranno_** aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2 e potrebbero non essere compatibili con le versioni più recenti di Unity.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md).

[Lo](../../../design/gaze-and-commit.md) sguardo è la prima forma di input e rivela la finalità e la consapevolezza dell'utente. MR Input 210 (noto Project Explorer) è un approfondimento dei concetti relativi allo sguardo per Windows Mixed Reality. Verrà aggiunta la consapevolezza contestuale al cursore e agli ologrammi, sfruttando al meglio ciò che l'app sa sullo sguardo dell'utente.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Qui è stato creato un astronauta che aiuta a apprendere i concetti relativi agli sguardi. In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md)era presente un semplice cursore che seguiva lo sguardo. Oggi si sposta un passaggio oltre il semplice cursore:

* Il cursore e gli ologrammi sono in grado di riconoscere lo sguardo: entrambi cambieranno in base alla posizione in cui l'utente sta cercando o alla posizione in cui l'utente *non sta* cercando. In questo modo sono in grado di riconoscere il contesto.
* Si aggiungeranno commenti e suggerimenti al cursore e agli ologrammi per fornire all'utente un contesto più ampio sugli elementi di destinazione. Questo feedback può essere audio e visivo.
* Verranno illustrate le tecniche di targeting per aiutare gli utenti a ottenere destinazioni più piccole.
* Verrà illustrato come attirare l'attenzione dell'utente verso gli ologrammi con un indicatore direzionale.
* Verranno illustrate le tecniche per portare gli ologrammi con l'utente mentre si sposta nel mondo.

>[!IMPORTANT]
>I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e Toolkit. Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile che nei video corrispondenti siano visualizzati script e oggetti visivi non aggiornati. I video rimangono inclusi per i poster e perché i concetti trattati sono ancora applicabili.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Input MR 210: Sguardo fisso</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un Windows 10 pc configurato con gli strumenti [corretti installati.](../../../develop/install-the-tools.md)
* Alcune funzionalità di programmazione C# di base.
* È necessario aver completato [MR Basics 101.](../../../develop/unity/tutorials/holograms-101.md)
* Un HoloLens configurato [per lo sviluppo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) richiesti dal progetto. Richiede Unity 2017.2 o versione successiva.
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è disponibile in GitHub [.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)

### <a name="errata-and-notes"></a>Errata e note

* In Visual Studio, "Just My Code" deve essere disabilitato (deselezionato) in Strumenti->Opzioni->Debug per poter accedere ai punti di interruzione nel codice.

## <a name="chapter-1---unity-setup"></a>Capitolo 1 - Installazione di Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Obiettivi

* Ottimizzare Unity per lo sviluppo di HoloLens.
* Importare gli asset e configurare la scena.
* Visualizzare l'astronauta nella HoloLens.

### <a name="instructions"></a>Istruzioni

1. Riavviare Unity.
2. Selezionare **Nuovo progetto**.
3. Assegnare al progetto **il nome ModelExplorer**.
4. Immettere il percorso come **cartella Gaze** precedentemente non archiviata.
5. Assicurati che il progetto sia impostato su **3D**.
6. Fare **clic su Crea Project**.

### <a name="unity-settings-for-hololens"></a>Impostazioni di Unity per HoloLens

È necessario invii a Unity che l'app che si sta tentando di esportare deve creare una visualizzazione [immersiva](../../../design/app-views.md) anziché una visualizzazione 2D. A tale scopo, è possibile aggiungere HoloLens come dispositivo di realtà virtuale.

1. Passare a **Modifica > Project Impostazioni > Lettore**.
2. Nel pannello **Inspector per** Player Impostazioni selezionare l'icona Windows **Store.**
3. Espandere il gruppo **Impostazioni XR**.
4. Nella sezione **Rendering** selezionare la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata) per aggiungere un nuovo elenco di **SDK per la realtà virtuale**.
5. Verificare che **Realtà mista di Windows** sia visualizzato nell'elenco. In caso contrario, selezionare **+** il pulsante nella parte inferiore dell'elenco e scegliere Windows **Holographic**.

Successivamente, è necessario impostare il back-end di scripting su .NET.

1. Passare a **Modifica > Project Impostazioni > Lettore** (potrebbe essere ancora presente nel passaggio precedente).
2. Nel pannello **Inspector per** Player Impostazioni selezionare l'icona Windows **Store.**
3. Nella sezione **Other Impostazioni** Configuration assicurarsi che **Scripting Back-End** sia impostato su **.NET**

Infine, aggiorneremo le impostazioni di qualità per ottenere prestazioni veloci in HoloLens.

1. Passare a **Modifica > Project Impostazioni > qualità**.
2. Fare clic sulla freccia rivolta verso il basso nella **riga Predefinita** sotto l'icona Windows Store.
3. Selezionare **Molto bassa per** app Windows **Store.**

### <a name="import-project-assets"></a>Importare asset di progetto

1. Fare clic con il **pulsante destro del mouse** sulla cartella **Assets Project** pannello.
2. Fare clic **su Importa pacchetto > pacchetto personalizzato**.
3. Passare ai file di progetto scaricati e fare clic **su ModelExplorer.unitypackage**.
4. Fare clic su **Apri**.
5. Dopo il caricamento del pacchetto, fare clic sul **pulsante** Importa.

### <a name="setup-the-scene"></a>Configurare la scena

1. Nella gerarchia eliminare la **fotocamera principale**.
2. Nella cartella **HoloToolkit** aprire la **cartella Input** e quindi aprire la **cartella Prefabs.**
3. Trascinare e rilasciare il prefab **MixedRealityCameraParent** dalla cartella **Prefabs** in **Hierarchy**.
4. Fare clic con il pulsante destro del mouse sulla **luce direzionale** nella gerarchia e scegliere **Elimina**.
5. Nella cartella **Ologrammi,** trascinare e rilasciare gli asset seguenti nella radice della **gerarchia**:
    * **AstroMan**
    * **Luci**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Avviare **la modalità di** ▶ per visualizzare l'astronauta.
7. Fare **clic su Modalità** ▶ di nuovo per **arrestare**.
8. Nella cartella **Ologrammi** trovare l'asset **Fitbox** e trascinarlo nella radice della **gerarchia**.
9. Selezionare **fitbox** nel **pannello Gerarchia.**
10. Trascinare **la raccolta AstroMan** dalla **gerarchia** alla proprietà **Raccolta ologrammi** di Fitbox nel **pannello Controllo.**

### <a name="save-the-project"></a>Salvare il progetto

1. Salvare la nuova scena: **File > Salva scena con nome**.
2. Fare **clic su Nuova cartella** e assegnare alla cartella il nome **Scenes**.
3. Assegnare al file **il nome " ModelExplorer**" e salvarlo nella **cartella Scenes.**

### <a name="build-the-project"></a>Compilare il progetto

1. In Unity selezionare **File > Build Impostazioni**.
2. Fare **clic su Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena.
3. Selezionare **Universal Windows Platform nell'elenco** Piattaforma **e** fare clic su **Cambia piattaforma.**
4. Se si sviluppa in modo specifico per HoloLens, impostare **Dispositivo di destinazione** su **HoloLens**. In caso contrario, lasciarlo in **Qualsiasi dispositivo.**
5. Assicurarsi **che Build Type (Tipo** di compilazione) sia impostato su **D3D** e **che SDK** sia impostato su Latest **installed** (Versione più recente installata), che deve essere SDK 16299 o versione successiva.
6. Fare clic su **Compila**.
7. Creare una **nuova cartella** denominata "App".
8. Fare clic sulla **cartella App.**
9. Fare clic **su Seleziona cartella**.

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

## <a name="chapter-2---cursor-and-target-feedback"></a>Capitolo 2 - Feedback su cursori e destinazione

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Obiettivi

* Progettazione visiva e comportamento del cursore.
* Feedback del cursore basato su sguardo fisso.
* Feedback dell'ologramma basato su sguardo fisso.

Il lavoro si baserà su alcuni principi di progettazione del cursore, in questo modo:

* Il cursore è sempre presente.
* Non lasciare che il cursore sia troppo piccolo o grande.
* Evitare di ostruire il contenuto.

### <a name="instructions"></a>Istruzioni

1. Nella cartella **HoloToolkit\Input\Prefabs** trovare l'asset **InputManager.**
2. Trascinare e rilasciare **InputManager** in **Hierarchy.**
3. Nella cartella **HoloToolkit\Input\Prefabs** trovare l'asset **Cursore.**
4. Trascinare e rilasciare **il cursore** sulla **gerarchia**.
5. Selezionare **l'oggetto InputManager** nella **gerarchia**.
6. Trascinare **l'oggetto Cursor** dalla **gerarchia** nel campo **Cursore** di **SimpleSinglePointerSelector** di InputManager, nella parte inferiore del **controllo**.

![Configurazione del selettore di puntatore singolo semplice](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Compilazione e distribuzione

1. Ricompilare l'app **da File > Build Impostazioni**.
2. Aprire la **cartella App**.
3. Aprire la **soluzione Visual Studio ModelExplorer**.
4. Fare **clic su Debug -> Avvia senza eseguire debug** o premere **CTRL+F5.**
5. Osservare come viene disegnato il cursore e come cambia aspetto se tocca un ologramma.

### <a name="instructions"></a>Istruzioni

1. Nel pannello **Hierarchy (Gerarchia)** espandi l'oggetto GEO_G Back_Center  ->  ->  AstroMan.
2. Fare doppio clic **su Interactible.cs** per aprirlo in Visual Studio.
3. Rimuovere il commento delle righe nei callback **IFocusable.OnFocusEnter()** e **IFocusable.OnFocusExit()** in **Interactible.cs**. Questi vengono chiamati da InputManager del Toolkit realtà mista quando lo stato attivo (tramite sguardo fisso o puntamento del controller) entra ed esce dal collisore del GameObject specifico.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>Viene utilizzato `EnableKeyword` e `DisableKeyword` superiore. Per usarli nella propria app con lo shader Standard di Toolkit, è necessario seguire le linee guida di Unity per l'accesso ai materiali [tramite script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). In questo caso, sono già [](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) state incluse le tre varianti del materiale evidenziato necessarie nella cartella Risorse (cercare i tre materiali con l'evidenziazione nel nome).

### <a name="build-and-deploy"></a>Compilazione e distribuzione

1. Come in precedenza, compilare il progetto e distribui HoloLens.
2. Osservare cosa accade quando lo sguardo punta a un oggetto e quando non lo è.

## <a name="chapter-3---targeting-techniques"></a>Capitolo 3 - Tecniche di destinazione

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Obiettivi

* Semplificare la destinazione degli ologrammi.
* Stabilizzare i movimenti naturali della testa.

### <a name="instructions"></a>Istruzioni

1. Nel pannello **Hierarchy (Gerarchia)** seleziona **l'oggetto InputManager.**
2. Nel pannello **Inspector (Controllo)** trova lo script **Gaze Stabilir (Stabilizzatore sguardo** fisso). Fare clic per aprirlo Visual Studio, se si vuole dare un'occhiata.
    * Questo script scorre campioni di dati Raycast e aiuta a stabilizzare lo sguardo dell'utente per la selezione della destinazione di precisione.
3. In **Inspector (Controllo)** è possibile modificare il **valore Stored Stability Samples (Esempi di stabilità** archiviati). Questo valore rappresenta il numero di campioni su cui lo stabilizzatore scorre per calcolare il valore stabilizzato.

## <a name="chapter-4---directional-indicator"></a>Capitolo 4 - Indicatore direzionale

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Obiettivi

* Aggiungere un indicatore direzionale sul cursore per facilitare la ricerca di ologrammi.

### <a name="instructions"></a>Istruzioni

Si userà il file **DirectionIndicator.cs** che:

1. Mostra l'indicatore direzionale se l'utente non guarda gli ologrammi.
2. Nascondere l'indicatore direzionale se l'utente guarda gli ologrammi.
3. Aggiornare l'indicatore direzionale in modo che punti agli ologrammi.

A questo punto, procedere con l'esercitazione.

1. Fare clic **sull'oggetto AstroMan** nel **pannello Hierarchy (Gerarchia)** e fare clic sulla **freccia** per espanderlo.
2. Nel pannello **Hierarchy (Gerarchia)** seleziona **l'oggetto DirectionalIndicator** in **AstroMan.**
3. Nel pannello **Inspector (Controllo)** fai clic **sul pulsante Add Component (Aggiungi** componente).
4. Nel menu digitare nella casella di ricerca **Indicatore di direzione**. Selezionare il risultato della ricerca.
5. Nel pannello **Hierarchy (Gerarchia)** trascinare e rilasciare l'oggetto **Cursor** sulla proprietà **Cursor** in **Inspector**.
6. Nel pannello **Project,** nella cartella **Ologrammi,** trascinare e rilasciare l'asset **DirectionalIndicator** sulla proprietà **Directional Indicator** in **Inspector**.
7. Compilare e distribuire l'app.
8. Osservare come l'oggetto indicatore direzionale consente di trovare l'astronauta.

## <a name="chapter-5---billboarding"></a>Capitolo 5 - Singing

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Obiettivi

* Usare l'uso dell'ologramma per avere sempre un viso verso l'utente.

Verrà utilizzato il file **Manifesto.cs per** mantenere un GameObject orientato in modo che sia sempre rivolto verso l'utente.

1. Nel pannello **Hierarchy (Gerarchia)** seleziona **l'oggetto AstroMan.**
2. Nel pannello **Inspector (Controllo)** fai clic **sul pulsante Add Component (Aggiungi** componente).
3. Nel menu digitare nella casella di ricerca **Il tempo di ricerca è .** Selezionare il risultato della ricerca.
4. In Inspector **(Controllo)** impostare **Asse pivot** su **Y.**
5. Prova Compilare e distribuire l'app come in precedenza.
6. Vedere il modo in cui l'oggetto Disartie viene visualizzato indipendentemente dal modo in cui cambi il punto di vista.
7. Eliminare lo script da **AstroMan** per il momento.

## <a name="chapter-6---tag-along"></a>Capitolo 6 - Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Obiettivi

* Usare Tag-Along per fare in modo che gli ologrammi ci seguano in tutta la stanza.

Quando si lavora a questo problema, si verrà guidati dai vincoli di progettazione seguenti:

* Il contenuto deve essere sempre a colpo d'occhio.
* Il contenuto non deve essere in alcun modo.
* Il contenuto con blocco della testa è inassato.

La soluzione usata in questo caso consiste nell'usare un approccio "tag-along".

Un oggetto tag-along non lascia mai completamente la visualizzazione dell'utente. È possibile pensare a un tag-along come a un oggetto collegato alla testa dell'utente da bande di gomma. Quando l'utente si sposta, il contenuto rimane a colpo d'occhio scorrendo verso il bordo della visualizzazione senza uscire completamente. Quando l'utente guarda verso l'oggetto tag-along, viene visualizzato in modo più completo.

Si userà il file **SimpleTagalong.cs** che:

1. Determinare se lTag-Along o object è all'interno dei limiti della fotocamera.
2. Se non si trova all'interno del frustum di visualizzazione, posizionare il Tag-Along parzialmente all'interno del frustum di visualizzazione.
3. In caso contrario, posizionare Tag-Along a una distanza predefinita dall'utente.

A tale scopo, è prima necessario modificare lo script **Interactible.cs** per chiamare **TagalongAction.**

1. Modificare **Interactible.cs completando** l'esercizio di codifica 6.a (rimuovere il commento dalle righe da 84 a 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

Lo script **InteractibleAction.cs,** associato a **Interactible.cs,** esegue azioni personalizzate quando si toccano gli ologrammi. In questo caso, ne verrà utilizzato uno specifico per il tag-along.

* Nella cartella **Scripts** fare clic **sull'asset TagalongAction.cs** per aprirlo in Visual Studio.
* Completare l'esercizio di scrittura del codice o modificarlo in questo modo:
  * Nella parte superiore di **Hierarchy (Gerarchia)** digitare ChestButton_Center **e** selezionare il risultato.
  * Nel pannello **Inspector (Controllo)** fai clic **sul pulsante Add Component (Aggiungi** componente).
  * Nel menu digitare nella casella di ricerca **Tagalong Action**. Selezionare il risultato della ricerca.
  * Nella **Ologrammi** trovare l'asset **Tagalong.**
  * Selezionare **l ChestButton_Center o** object nella **gerarchia**. Trascinare e **rilasciare l'oggetto TagAlong** dal  **pannello Project** controllo nella proprietà Object To **Tagalong (Da** oggetto a tag).
  * Trascinare **l'oggetto Tagalong Action** da **Inspector nel** campo **Interactible Action** dello script **Interactible.**
* Fare doppio clic **su tagalongAction** script per aprirlo in Visual Studio.

![Configurazione di interactible](images/holograms210-interactible.png)

È necessario aggiungere quanto segue:

* Aggiungere funzionalità alla funzione PerformAction nello script TagalongAction (ereditato da InteractibleAction).
* Aggiungere un'etichetta all'oggetto con sguardo fisso e impostare l'asse pivot su XY.
* Aggiungere quindi una Tag-Along semplice all'oggetto .

Ecco la soluzione, da **TagalongAction.cs:**

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* Prova Compilare e distribuire l'app.
* Osservare come il contenuto segue il centro del punto di sguardo fisso, ma non continuamente e senza bloccarlo.