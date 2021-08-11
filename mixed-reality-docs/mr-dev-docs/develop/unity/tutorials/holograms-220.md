---
title: HoloLens (prima generazione) Spaziale 220 - Audio spaziale
description: Seguire questa procedura dettagliata per la scrittura di codice usando Unity, Visual Studio e HoloLens informazioni dettagliate sui concetti relativi al suono spaziale.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, spatial sound, HoloLens, Mixed Reality Academy, unity, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale, Windows 10
ms.openlocfilehash: d53b449916405d8bf42bb8dd63cc1d3cb5d6127bbf9b2989ce7cb09c3762a6e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200376"
---
# <a name="hololens-1st-gen-spatial-220-spatial-sound"></a>HoloLens (prima generazione) Spaziale 220: Audio spaziale

>[!IMPORTANT]
>Le esercitazioni di Mixed Reality Academy sono state progettate per HoloLens (prima generazione), Unity 2017 e visori VR immersive di Realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi. Queste esercitazioni non **_verranno_** aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2 e potrebbero non essere compatibili con le versioni più recenti di Unity.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md).

[Il suono](../../../design/spatial-sound.md) spaziale trasforma la vita in ologrammi e offre loro la presenza nel mondo. Ologrammi sono costituiti da luce e suono e se si perde di vista gli ologrammi, l'audio spaziale può aiutare a trovarli. L'audio spaziale non è simile al suono tipico che si udirebbe alla radio, ma è un suono posizionato nello spazio 3D. Con l'audio spaziale, è possibile far sembrare che gli ologrammi siano dietro di te, accanto a te o persino in testa. In questo corso:

* Configurare l'ambiente di sviluppo per l'uso di Microsoft Spatial Sound.
* Usare l'audio spaziale per migliorare le interazioni.
* Usare l'audio spaziale in combinazione [con Il mapping spaziale](../../../design/spatial-mapping.md).
* Comprendere la progettazione del suono e la combinazione di procedure consigliate.
* Usa il suono per migliorare gli effetti speciali e portare l'utente nel mondo della realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Spaziale MR 220: Audio spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un Windows 10 pc configurato con gli strumenti [corretti installati.](../../../develop/install-the-tools.md)
* Alcune funzionalità di programmazione C# di base.
* È necessario aver completato [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* Un HoloLens configurato [per lo sviluppo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) richiesti dal progetto. Richiede Unity 2017.2 o versione successiva.
  * Se è ancora necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Questa versione potrebbe non essere più aggiornata.
  * Se è ancora necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Questa versione potrebbe non essere più aggiornata.
  * Se è ancora necessario il supporto di Unity 5.4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Questa versione potrebbe non essere più aggiornata.
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facilmente raggiungibile.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è disponibile [in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Errata e note

* "Abilita Just My Code" deve essere disabilitato *(* deselezionato ) in Visual Studio in Strumenti->Opzioni -debug >per poter terminare con i punti di interruzione nel codice.

## <a name="chapter-1---unity-setup"></a>Capitolo 1- Configurazione di Unity

### <a name="objectives"></a>Obiettivi

* Modificare la configurazione audio di Unity per usare Microsoft Spatial Sound.
* Aggiungere un suono 3D a un oggetto in Unity.

### <a name="instructions"></a>Istruzioni

* Riavviare Unity.
* Selezionare **Open** (Apri).
* Passare al desktop e trovare la cartella precedentemente non archiviata.
* Fare clic sulla **cartella Starting\Decibel** e quindi fare clic **sul pulsante Seleziona** cartella.
* Attendere il caricamento del progetto in Unity.
* Nel pannello **Project** aprire **Scenes\Decibel.unity.**
* Nel pannello **Hierarchy (Gerarchia)** espandi **HologramCollection** e seleziona **P0LY.**
* In Inspector (Controllo) espandere **AudioSource** e notare che non è presente alcuna **casella di controllo Spatialize** (Spazializza).

Per impostazione predefinita, Unity non carica un plug-in di spazializzatore. La procedura seguente abiliterà l'audio spaziale nel progetto.

* Nel menu in alto di Unity passare a **Edit > Project Impostazioni > Audio (Modifica audio).**
* Trovare **l'elenco a discesa Spatializer Plugin (Plug-in** spazializzatore) e selezionare **MS HRTF Spatializer (Spazializzatore MS HRTF).**
* Nel pannello **Hierarchy (Gerarchia)** seleziona **HologramCollection > P0LY**.
* Nel pannello **Inspector** (Controllo) trova il **componente Audio Source (Origine** audio).
* Selezionare la casella **di controllo Spazializza.**
* Trascinare **il dispositivo di scorrimento** Spatial Blend fino a **3D** oppure **immettere 1** nella casella di modifica.

Il progetto verrà ora compilato in Unity e la soluzione verrà configurata in Visual Studio.

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
2. Aprire la **soluzione Visual Studio Decibel**.

Se si esegue la distribuzione HoloLens:

1. Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Release** e da ARM a **x86.**
2. Fare clic sulla freccia a discesa accanto al pulsante Computer locale e selezionare **Computer remoto.**
3. Immettere **l'HoloLens IP del dispositivo** e impostare Modalità di autenticazione su Universale **(protocollo non crittografato).** Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, Impostazioni > rete & **Internet > Opzioni avanzate**.
4. Nella barra dei menu superiore fare clic **su Debug -> Avvia** senza eseguire debug oppure premere **CTRL+F5.** Se è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarlo a Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).

Se si esegue la distribuzione in un visore VR immersive:

1. Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Release** e da ARM a **x64.**
2. Assicurarsi che la destinazione di distribuzione sia impostata **su Computer locale.**
3. Nella barra dei menu superiore fare clic **su Debug -> Avvia** senza eseguire debug oppure premere **CTRL+F5.**

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capitolo 2 - Audio spaziale e interazione

### <a name="objectives"></a>Obiettivi

* Migliorare il sound dell'ologramma usando il suono.
* Indirizzare lo sguardo fisso dell'utente usando il suono.
* Fornire feedback sui movimenti usando l'audio.

### <a name="part-1---enhancing-realism"></a>Parte 1: Miglioramento di Un'altra parte

#### <a name="key-concepts"></a>Concetti chiave

* Spazializzare i suoni dell'ologramma.
* Le sorgenti sonore devono essere posizionate in una posizione appropriata nell'ologramma.

La posizione appropriata per il suono dipenderà dall'ologramma. Ad esempio, se l'ologramma è di un essere umano, la sorgente audio deve trovarsi vicino alla terra e non ai piedi.

#### <a name="instructions"></a>Istruzioni

Le istruzioni seguenti collegano un suono spazializzato a un ologramma.

* Nel pannello **Hierarchy (Gerarchia)** espandi **HologramCollection** e seleziona **P0LY.**
* Nel pannello **Inspector** (Controllo) in **AudioSource fare** clic sul cerchio accanto a **AudioClip (AudioClip)** e selezionare **PolyHover** dal popup.
* Fare clic sul cerchio accanto **a Output** e **selezionare SoundEffects** dal popup.

Project Decibel usa un componente **AudioMixer** di Unity per abilitare la regolazione dei livelli audio per gruppi di suoni. Raggruppando i suoni in questo modo, è possibile regolare il volume complessivo mantenendo il volume relativo di ogni suono.

* In **AudioSource espandere** **3D Sound Impostazioni**.
* Impostare **Doppler Level (Livello Doppler)** **su 0.**

L'impostazione del livello Doppler su zero disabilita le modifiche del passo causate dal movimento (dell'ologramma o dell'utente). Un esempio classico di Doppler è un'auto in rapida movimento. Quando l'auto si avvicina a un listener zionario, il passo del motore aumenta. Quando passa l'listener, il passo si riduce con la distanza.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2: Indirizzare lo sguardo fisso dell'utente

#### <a name="key-concepts"></a>Concetti chiave

* Usare il suono per richiamare l'attenzione su ologrammi importanti.
* Le eseree aiutano a indirizzare il punto in cui devono apparire gli occhi.
* Il cervello ha alcune aspettative apprese.

Un esempio di aspettative apprese è che gli animali sono in genere al di sopra delle teste degli esseri umani. Se un utente ascolta un suono di un volatile, la reazione iniziale è cercare. Posizionando un volatile sotto l'utente, l'utente può far fronte alla direzione corretta del suono, ma non riesce a trovare l'ologramma in base alla previsione di dover cercare.

#### <a name="instructions"></a>Istruzioni

Le istruzioni seguenti consentono a P0LY di nascondersi dietro l'utente, in modo che sia possibile usare l'audio per individuare l'ologramma.

* Nel pannello **Hierarchy (Gerarchia)** selezionare Managers **(Responsabili).**
* Nel pannello **Inspector (Controllo)** trovare **Speech Input Handler (Gestore input vocale).**
* In **Speech Input Handler (Gestore input vocale)** espandere Go Hide **(Nascondi).**
* Modificare **No Function (Nessuna** **funzione) in PolyActions.GoHide**.

![Parola chiave: Vai a Nascondi](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3: Feedback dei movimenti

#### <a name="key-concepts"></a>Concetti chiave

* Fornire all'utente la conferma del movimento positivo usando il suono
* Non sovraccaricare l'utente: i suoni esatti vengono intasati
* I suoni più piccoli funzionano meglio: non sovrastogliere l'esperienza

#### <a name="instructions"></a>Istruzioni

* Nel pannello **Hierarchy (Gerarchia)** espandere **HologramCollection.**
* Espandere **EnergyHub** e selezionare **Base**.
* Nel pannello **Inspector (Controllo)** fai clic **su Add Component (Aggiungi componente)** e aggiungi **Gesture Sound Handler (Gestore audio movimento).**
* In **Gesture Sound Handler (Gestore** del suono del movimento) fai clic sul cerchio accanto a Navigation Started **Clip** (Clip avviato di navigazione) e Navigation **Updated Clip** (Clip aggiornato di navigazione) e seleziona RotateClick (Ruota)Click dal popup per entrambi. 
* Fare doppio clic su "GestureSoundHandler" per carica Visual Studio.

Gesture Sound Handler esegue le attività seguenti:

* Creare e configurare un **oggetto AudioSource.**
* Posizionare **AudioSource nella** posizione dell'oggetto **GameObject appropriato.**
* Riproduce **l'oggetto AudioClip** associato al movimento.

#### <a name="build-and-deploy"></a>Compilazione e distribuzione

1. In Unity selezionare **File > Build Impostazioni**.
2. Fare clic su **Compila**.
3. Fare clic sulla **cartella App.**
4. Fare clic **su Seleziona cartella**.

Verificare che la barra degli strumenti sia "Release", "x86" o "x64" e "Remote Device". In caso contrario, si tratta dell'istanza di codifica di Visual Studio. Potrebbe essere necessario aprire nuovamente la soluzione dalla cartella App.

* Se richiesto, ricaricare i file di progetto.
* Come in precedenza, eseguire la distribuzione da Visual Studio.

Dopo la distribuzione dell'applicazione:

* Osservare come cambia il suono mentre ci si sposta intorno a P0LY.
* Pronunciare *"Vai a nascondi"* per fare in modo che P0LY si sposti in una posizione dietro l'utente. Trovarlo in base al suono.
* Osservare la base dell'hub energetico. Toccare e trascinare verso sinistra o destra per ruotare l'ologramma e osservare come il suono del clic conferma il movimento.

Nota: è disponibile un pannello di testo che verrà associato all'utente. Conterrà i comandi vocali disponibili che è possibile usare in questo corso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capitolo 3 - Audio spaziale e mapping spaziale

### <a name="objectives"></a>Obiettivi

* Confermare l'interazione tra ologrammi e il mondo reale usando il suono.
* Occlude sound using the physical world ( Occlude audio using the physical world).

### <a name="part-1---physical-world-interaction"></a>Parte 1 - Interazione fisica con il mondo

#### <a name="key-concepts"></a>Concetti chiave

* Gli oggetti fisici in genere fanno un suono quando si incontra una superficie o un altro oggetto.
* I suoni devono essere appropriati per il contesto all'interno dell'esperienza.

Ad esempio, l'impostazione di una tazzina su un tavolo dovrebbe rendere un suono più silenzioso rispetto all'eliminazione di una tazzina su un elemento di metal.

#### <a name="instructions"></a>Istruzioni

* Nel pannello **Hierarchy (Gerarchia)** espandere **HologramCollection.**
* Espandere **EnergyHub** e selezionare **Base.**
* Nel pannello **Inspector (Controllo)** fai clic **su Add Component (Aggiungi** componente) e aggiungi Tap To Place With Sound and Action (Tocca per posizionare con suono e **azione).**
* In Tap to Place With Sound and Action (Toccare per **posizionare con audio e azione):**
  * Selezionare **Place Parent (Inserisci elemento padre) al tocco.**
  * Impostare **Suono di posizionamento** su **Posiziona**.
  * Impostare **Pickup Sound (Suono ritiro)** su Pickup **(Ritiro).**
  * Premere + in basso a destra in Azione al ritiro **e** **Su azione di posizionamento**. Trascinare EnergyHub dalla scena nei **campi Nessuno (oggetto).**
    * In **On Pickup Action (All'azione di** ritiro) fare clic su No Function EnergyHubBase ResetAnimation (Nessuna **funzione**  ->  **EnergyHubBase**  ->  **ResetAnimation).**
    * In **On Placement Action (All'azione di** posizionamento) fare clic su No Function EnergyHubBase OnSelect (Nessuna **funzione**  ->  **EnergyHubBase**  ->  **OnSelect).**

![Toccare To Place with Sound and Action (Posizione con suono e azione)](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2 - Occlusione del suono

#### <a name="key-concepts"></a>Concetti chiave

* Il suono, come la luce, può essere occluded.

Un esempio classico è una sala da concerto. Quando un listener è in piedi all'esterno della sala e la porta è chiusa, la musica sembra ovattata. In genere si verifica anche una riduzione del volume. Quando la porta viene aperta, viene udita l'intera gamma del suono al volume effettivo. I suoni ad alta frequenza sono in genere più elevati delle frequenze basse.

#### <a name="instructions"></a>Istruzioni

* Nel pannello **Hierarchy (Gerarchia)** espandi **HologramCollection** e seleziona **P0LY.**
* Nel pannello **Inspector (Controllo)** fare clic **su Add Component (Aggiungi componente)** e aggiungere Audio **Emitter (Emettitore audio).**

La classe Audio Emitter offre le funzionalità seguenti:

* Ripristina tutte le modifiche apportate al volume di **AudioSource.**
* Esegue **un oggetto Physics.RaycastNonAlloc** dalla posizione dell'utente nella direzione del **GameObject** a cui è collegato **AudioEmitter.**

Il metodo RaycastNonAlloc viene usato come ottimizzazione delle prestazioni per limitare le allocazioni e il numero di risultati restituiti.

* Per ogni **IAudioInfluencer** rilevato, chiama il **metodo ApplyEffect.**
* Per ogni **IAudioInfluencer precedente** che non viene più rilevato, chiamare il **metodo RemoveEffect.**

Si noti che AudioEmitter viene aggiornato sulle scale temporate umane, anziché per ogni fotogramma. Ciò avviene perché gli esseri umani in genere non si spostano abbastanza velocemente perché l'effetto deve essere aggiornato più frequentemente rispetto a ogni trimestre o metà di secondo. Ologrammi teletrasporto rapido da una posizione a un'altra può interrompere l'illusione.

* Nel pannello **Gerarchia** espandere **HologramCollection**.
* Espandere **EnergyHub** e selezionare **BlobOutside.**
* Nel pannello **Inspector** (Controllo) fare **clic su Add Component** (Aggiungi componente) e aggiungere Audio **Occluder (Occluder audio).**
* In **Audio Occluder** impostare **Cutoff Frequency** su **1500**.

Questa impostazione limita le frequenze AudioSource a 1500 Hz e inferiori.

* Impostare **Passaggio del volume** su **0,9**.

Questa impostazione riduce il volume di AudioSource al 90% del livello corrente.

Audio Occluder implementa IAudioInfluencer per:

* Applicare un effetto di occlusione usando **un oggetto AudioLowPassFilter** che viene collegato all'oggetto **AudioSource** gestito acquistare **AudioEmitter.**
* Applica l'attenuazione del volume a AudioSource.
* Disabilita l'effetto impostando una frequenza di cutoff neutra e disabilitando il filtro.

La frequenza usata come neutra è di 22 kHz (22000 Hz). Questa frequenza è stata scelta perché è superiore alla frequenza massima nominale che può essere ascoltata dall'udito umano, senza alcun impatto percepibile sul suono.

* Nel pannello **Gerarchia** selezionare **SpatialMapping**.
* Nel pannello **Inspector** (Controllo) fare **clic su Add Component** (Aggiungi componente) e aggiungere Audio **Occluder (Occluder audio).**
* In **Audio Occluder** impostare **Cutoff Frequency** su **750.**

Quando più occluder si trova nel percorso tra l'utente e **AudioEmitter,** al filtro viene applicata la frequenza più bassa.

* Impostare **Passaggio del volume** su **0,75**.

Quando più occluder si trova nel percorso tra l'utente e **AudioEmitter,** il pass-through del volume viene applicato in modo additivo.

* Nel pannello **Gerarchia** selezionare **Manager**.
* Nel pannello **Inspector (Controllo)** espandere **Speech Input Handler (Gestore input voce).**
* In **Gestore input vocale** espandere Go **Charge**.
* Impostare **Nessuna funzione** su **PolyActions.GoCharge**.

![Parola chiave: Go Charge](images/gocharge.png)

* Espandere **Come qui**.
* Impostare **Nessuna funzione** su **PolyActions.ComeBack**.

![Parola chiave: Come Here](images/comehere.png)

#### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Come in precedenza, compilare il progetto in Unity e distribuirsi in Visual Studio.

Dopo la distribuzione dell'applicazione:

* Pronunciare *"Go Charge"* per fare in modo che P0LY immissione nell'hub energetico.

Si noti la modifica nel suono. Dovrebbe sembrare ovattato e un po' più silenzioso. Se si è in grado di posizionarsi con una parete o un altro oggetto tra l'utente e l'hub energetico, si noterà un'ulteriore modifica del suono a causa dell'occlusione da parte del mondo reale.

* Pronunciare *"Come Here"* per fare in modo che P0LY lasci l'hub energetico e si posizioni davanti a sé.

Si noti che l'occlusione audio viene rimossa quando P0LY esce dall'hub energetico. Se si è ancora in ascolto dell'occlusione, P0LY potrebbe essere occluso dal mondo reale. Provare a passare a P0LY per assicurarsi di avere una linea di vista chiara.

### <a name="part-3---room-models"></a>Parte 3 - Modelli di stanza

#### <a name="key-concepts"></a>Concetti chiave

* Le dimensioni dello spazio forniscono code subliminali che contribuiscono alla localizzazione del suono.
* I modelli di stanza vengono impostati in base a **AudioSource.**
* [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce il codice per l'impostazione del modello di stanza.
* Per esperienze di realtà mista, selezionare il modello di stanza più adatto allo spazio reale.

Se si crea uno scenario di realtà virtuale, selezionare il modello di stanza più adatto all'ambiente virtuale.

## <a name="chapter-4---sound-design"></a>Capitolo 4 - Sound Design

### <a name="objectives"></a>Obiettivi

* Informazioni sulle considerazioni per una progettazione efficace del suono.
* Informazioni sulla combinazione di tecniche e linee guida.

### <a name="part-1---sound-and-experience-design"></a>Parte 1 - Progettazione di suoni ed esperienze

In questa sezione vengono illustrate le considerazioni e le linee guida per la progettazione di elementi sonori e di esperienza chiave.

#### <a name="normalize-all-sounds"></a>Normalizzare tutti i suoni

In questo modo si evita la necessità di codice caso speciale per regolare i livelli di volume per suono, che può richiedere molto tempo e limita la possibilità di aggiornare facilmente i file audio.

#### <a name="design-for-an-untethered-experience"></a>Progettare per un'esperienza senzathering

HoloLens è un computer olografico completamente indipendente e senzathering. Gli utenti possono e useranno le esperienze durante lo spostamento. Assicurarsi di testare la combinazione di audio in modo da potersi aggirare.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emettere audio da posizioni logiche sugli ologrammi

Nel mondo reale, un cane non sbava dalla coda e la voce di un essere umano non viene dai suoi piedi. Evitare che i suoni emettono da parti impreviste degli ologrammi.

Per gli ologrammi di piccole dimensioni, è ragionevole avere emettere suoni dal centro della geometria.

#### <a name="familiar-sounds-are-most-localizable"></a>I suoni familiari sono più localizzabili

La voce umana e la musica sono molto facili da localizzare. Se qualcuno chiama il tuo nome, puoi determinare in modo molto accurato da quale direzione proveniva la voce e da quanto lontano. I suoni brevi e sconosciuti sono più difficili da localizzare.

#### <a name="be-cognizant-of-user-expectations"></a>Essere consci delle aspettative degli utenti

L'esperienza di vita ha un ruolo nella capacità di identificare la posizione di un suono. Questo è uno dei motivi per cui la voce umana è particolarmente facile da localizzare. È importante tenere presenti le aspettative apprese dall'utente quando inserisce i suoni.

Ad esempio, quando qualcuno ascolta un canto degli volatili, in genere cerca, perché gli animali tendono a essere sopra la linea di vista (in volo o in un albero). Non è insolito che un utente si trasformi nella direzione corretta di un suono, ma si trovi nella direzione verticale errata e diventi confuso o frustrato quando non riesce a trovare l'ologramma.

#### <a name="avoid-hidden-emitters"></a>Evitare emettitori nascosti

Nel mondo reale, se si ascolta un suono, è in genere possibile identificare l'oggetto che emette il suono. Questo dovrebbe valere anche nelle esperienze. Può essere molto sconcertante per gli utenti ascoltare un suono, sapere da dove ha origine il suono e non essere in grado di visualizzare un oggetto.

Esistono alcune eccezioni a questa linea guida. Ad esempio, i suoni di ambiente, ad esempio i cricket in un campo, non devono essere visibili. L'esperienza di vita ci offre familiarità con l'origine di questi suoni senza la necessità di vederla.

### <a name="part-2---sound-mixing"></a>Parte 2 - Combinazione di suoni

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Scegliere come destinazione la combinazione per il 70% del volume HoloLens

Le esperienze di realtà mista consentono di visualizzare gli ologrammi nel mondo reale. Devono anche consentire l'udito dei suoni reali. Una destinazione del volume del 70% consente all'utente di ascoltare il mondo che li circonda insieme al suono dell'esperienza.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens volume al 100% dovrebbe affogare i suoni esterni

Un livello di volume del 100% è simile a un'esperienza di realtà virtuale. Visivamente, l'utente viene trasportato in un mondo diverso. Lo stesso dovrebbe essere vero in modo udibile.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Usare Unity AudioMixer per regolare categorie di suoni

Quando si progetta la combinazione, è spesso utile creare categorie sonore e avere la possibilità di aumentare o ridurre il volume come unità. In questo modo vengono mantenuti i livelli relativi di ogni suono, consentendo al tempo stesso modifiche rapide e semplici alla combinazione complessiva. Le categorie comuni includono; effetti sonori, ambiente, voice over e musica di sottofondo.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Combinare suoni in base al sguardo dell'utente

Spesso può essere utile modificare la combinazione di suoni nell'esperienza in base alla posizione in cui un utente sta (o non sta) cercando. Un uso comune di questa tecnica consiste nel ridurre il livello di volume per gli ologrammi esterni al frame olografico per rendere più semplice per l'utente concentrarsi sulle informazioni di fronte a essi. Un altro uso è quello di aumentare il volume di un suono per attirare l'attenzione dell'utente su un evento importante.

#### <a name="building-your-mix"></a>Compilazione della combinazione

Quando si compila la combinazione, è consigliabile iniziare con l'audio di sottofondo dell'esperienza e aggiungere livelli in base all'importanza. In genere, ogni livello risulta più alto rispetto al precedente.

Immaginando il mix come imbuto invertito, con i suoni meno importanti (e in genere più silenziosi) nella parte inferiore, è consigliabile strutturare il mix in modo simile al diagramma seguente.

![Struttura della combinazione di suoni](images/soundlevels.png)

I voice over sono uno scenario interessante. In base all'esperienza che si sta creando, potrebbe essere necessario disporre di un suono stereo (non localizzato) o di spazializzare la voce over. Due esperienze pubblicate da Microsoft illustrano esempi eccellenti di ogni scenario.

[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voce stereo. Quando l'Assistente vocale descrive la posizione visualizzata, il suono è coerente e non varia in base alla posizione dell'utente. In questo modo l'assistente vocale può descrivere la scena senza allontanarsi dai suoni spazializzati dell'ambiente.

[I frammenti](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizzano una voce spaziale sotto forma di detective. La voce del detective viene usata per aiutare a portare l'attenzione dell'utente su un indizio importante come se un umano effettivo fosse nella stanza. Ciò consente un'esperienza ancora più immersiva nell'esperienza di risoluzione del problema.

### <a name="part-3--performance"></a>Parte 3 - Prestazioni

#### <a name="cpu-usage"></a>Utilizzo CPU

Quando si usa Il suono spaziale, 10 - 12 emettitori consumeranno circa il 12% della CPU.

#### <a name="stream-long-audio-files"></a>Trasmettere file audio lunghi

I dati audio possono essere di grandi dimensioni, in particolare a frequenze di campionamento comuni (44,1 e 48 kHz). Una regola generale è che i file audio più lunghi di 5-10 secondi devono essere trasmessi per ridurre l'utilizzo della memoria dell'applicazione.

In Unity è possibile contrassegnare un file audio per lo streaming nelle impostazioni di importazione del file.

![Impostazioni di importazione audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capitolo 5 - Effetti speciali

### <a name="objectives"></a>Obiettivi

* Aggiungere profondità a "Magic Windows".
* Portare l'utente nel mondo virtuale.

### <a name="magic-windows"></a>Magic Windows

#### <a name="key-concepts"></a>Concetti chiave

* La creazione di visualizzazioni in un mondo nascosto è visivamente interessante.
* Migliorare il realistico aggiungendo effetti audio quando un ologramma o l'utente si trova vicino al mondo nascosto.

#### <a name="instructions"></a>Istruzioni

* Nel pannello **Gerarchia** espandere **HologramCollection e** selezionare **Underworld.**
* Espandere **Underworld** e selezionare **VoiceSource.**
* Nel pannello **Inspector (Controllo)** fare **clic su Add Component (Aggiungi componente)** e aggiungere **User Voice Effect (Effetto voce utente).**

Un **componente AudioSource** verrà aggiunto a **VoiceSource.**

* In **AudioSource** impostare **Output** su **UserVoice (Mixer)**.
* Selezionare la **casella di controllo Spazializza.**
* Trascinare **il dispositivo di** scorrimento Spatial Blend fino a **3D** oppure **immettere 1** nella casella di modifica.
* Espandere **3D Sound Impostazioni**.
* Impostare **Livello Doppler** su **0.**
* In **User Voice Effect (Effetto** voce utente) impostare Parent Object **(Oggetto** padre) **su Underworld** dalla scena.
* Impostare **Distanza massima** su **1.**

**L'impostazione di Distanza** massima indica all'utente **l'effetto** vocale che l'utente deve essere vicino all'oggetto padre prima che l'effetto sia abilitato.

* In **User Voice Effect (Effetto voce utente)** espandere Coro Parameters **(Parametri coro).**
* Impostare **Profondità** su **0,1**.
* Impostare **Toccare 1 Volume,** **Toccare 2 Volume** e Toccare **3 Volume** su **0,8**.
* Impostare **Volume audio originale** su **0,5**.

Le impostazioni precedenti configurano i parametri di Unity **AudioChorusFilter** usato per aggiungere funzionalità avanzate alla voce dell'utente.

* In **User Voice Effect (Effetto** voce utente) espandere Echo Parameters **(Parametri Echo).**
* Impostare **Delay** su **300**
* Impostare **Rapporto di decadimento** **su 0,2**.
* Impostare **Volume audio originale** su **0.**

Le impostazioni precedenti configurano i parametri di Unity **AudioEchoFilter** usati per far sì che la voce dell'utente riecheggia.

Lo script User Voice Effect è responsabile di:

* Misurazione della distanza tra l'utente e **GameObject** a cui è collegato lo script.
* Determinare se l'utente deve o meno affrontare **GameObject.**

L'utente deve affrontare GameObject, indipendentemente dalla distanza, perché l'effetto sia abilitato.

* Applicazione e configurazione di **audioChorusFilter** e **AudioEchoFilter** a **AudioSource**.
* Disabilitazione dell'effetto disabilitando i filtri.

User Voice Effect usa il componente Mic Stream Selector, da [MixedRealityToolkit per Unity,](https://github.com/Microsoft/MixedRealityToolkit-Unity)per selezionare il flusso vocale di alta qualità e indirizzarlo al sistema audio di Unity.

* Nel pannello **Gerarchia** selezionare **Manager**.
* Nel pannello **Inspector (Controllo)** espandere **Speech Input Handler (Gestore input voce).**
* In **Speech Input Handler (Gestore input vocale)** espandere Show **Underworld (Mostra underworld).**
* Impostare **Nessuna funzione** su **UnderworldBase.OnEnable**.

![Parola chiave: Show Underworld](images/showunderworld.png)

* Espandere **Nascondi Underworld**.
* Impostare **Nessuna funzione** su **UnderworldBase.OnDisable**.

![Parola chiave: Hide Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Come in precedenza, compilare il progetto in Unity e distribuirsi in Visual Studio.

Dopo la distribuzione dell'applicazione:

* Affrontare una superficie (parete, piano, tabella) e *pronunciare "Show Underworld".*

Verrà visualizzato il mondo inferocito e tutti gli altri ologrammi verranno nascosti. Se non si vedono gli inferi, assicurarsi di affrontare una superficie reale.

* Avvicinati a 1 metro dall'ologramma degli inferi e inizia a parlare.

Sono ora disponibili effetti audio applicati alla voce.

* Allontanarsi dagli inferi e notare come l'effetto non viene più applicato.
* Pronunciare *"Hide Underworld"* per nascondere gli inferi.

Gli inferi saranno nascosti e gli ologrammi precedentemente nascosti verranno nuovamente visibili.

## <a name="the-end"></a>La fine

Congratulazioni! A questo punto è stato **completato MR Spatial 220: Spatial sound**.

Ascoltare il mondo e dare vita alle proprie esperienze con il suono.