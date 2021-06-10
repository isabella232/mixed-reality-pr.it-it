---
title: Impostazioni consigliate per Unity
description: Informazioni sui comportamenti di pubblicazione e prestazioni di Unity specifici per le app di realtà mista che possono essere attivate o disattivate tramite le impostazioni del progetto.
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: unity, impostazioni, realtà mista, HoloLens, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, prestazioni, impostazioni di qualità, impostazioni di illuminazione, buffer di profondità, xr, perdita di rilevamento
ms.openlocfilehash: 7516ec89c49a12e7cb143d7e53d00efde0e44c4e
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743387"
---
# <a name="recommended-settings-for-unity"></a>Impostazioni consigliate per Unity

Unity offre un set di opzioni predefinite che sono in genere il caso medio per tutte le piattaforme. Unity offre tuttavia alcuni comportamenti specifici della realtà mista che possono essere attivati o disattivati tramite le impostazioni del progetto.

## <a name="performant-environment-set-up"></a>Configurazione dell'ambiente a prestazioni performanti

### <a name="low-quality-settings"></a>Impostazioni di bassa qualità

È importante modificare le impostazioni di Qualità di **Unity** in **Molto** bassa in modo che l'applicazione venga eseguita e funzioni bene con la frequenza dei fotogrammi appropriata, in particolare per lo sviluppo di HoloLens. Per lo sviluppo con visori VR immersive, a seconda delle specifiche del desktop che alimentato l'esperienza di realtà virtuale, è comunque possibile ottenere la frequenza dei fotogrammi senza i parametri di qualità più bassa.

In Unity 2019 LTS+, è possibile impostare il livello di qualità del progetto selezionando **Edit** Project Settings Quality (Modifica qualità impostazioni progetto) e impostando Default (Predefinito) facendo clic sulla freccia verso il basso sul  >    >   **Very Low-quality level  (Livello di qualità molto basso).

### <a name="lighting-settings"></a>Impostazioni di illuminazione

Analogamente alle impostazioni della scena Qualità, è importante impostare le impostazioni di illuminazione ottimali per l'applicazione di realtà mista. In Unity, l'impostazione Di illuminazione che in genere avrà l'impatto maggiore sulle prestazioni della scena è Illuminazione globale in **tempo reale.** È possibile disattivare l'illuminazione globale selezionando Impostazioni di illuminazione di Rendering finestre  >    >    >  **Realtime Global Illumination (Illuminazione globale in tempo reale).**

È presente un'altra impostazione di illuminazione, **Baked Global Illumination.** Questa impostazione può fornire risultati accattivanti e visivamente accattivanti nei visori VR immersive, ma non è applicabile per lo sviluppo di HoloLens. **L'illuminazione** globale con bake viene calcolata solo per i GameObject statici, che non si trovano nelle scene di HoloLens a causa della natura di un ambiente sconosciuto e in continua evoluzione.

Per altre informazioni, leggere Global [Illumination from Unity](https://docs.unity3d.com/Manual/GIIntro.html) (Illuminazione globale da Unity). 

>[!NOTE]
> **L'illuminazione globale in tempo** reale è **impostata per** ogni scena e pertanto gli sviluppatori devono salvare questa proprietà per ogni scena Unity nel progetto.

### <a name="single-pass-instancing-rendering-path"></a>Percorso di rendering di istanze a passaggio singolo

Nelle applicazioni di realtà mista il rendering della scena viene eseguito due volte, una volta per ogni occhio dell'utente. Rispetto allo sviluppo 3D tradizionale, ciò raddoppia di fatto la quantità di lavoro che deve essere calcolata. È importante selezionare il percorso di rendering più efficiente in Unity per risparmiare tempo sia sulla CPU che sulla GPU. Il rendering con istanze a singolo passaggio ottimizza la pipeline di rendering unity per le app di realtà mista ed è consigliabile abilitare questa impostazione per impostazione predefinita per ogni progetto.

Per abilitare questa funzionalità nel tuo progetto Unity

1)  Apri **Player XR Settings** (Impostazioni XR riproduttore). A tale scopo, vai a **Edit** (Modifica) > **Project Settings** (Impostazioni progetto) > **Player** (Riproduttore) > **XR Settings** (Impostazioni XR)
2) Scegli **Single Pass Instanced** (Con istanze a singolo passaggio) dal menu a discesa **Stereo Rendering Method** (Metodo di rendering stereo). Deve essere selezionata la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata)

Per altri dettagli su questo approccio di rendering, leggere gli articoli seguenti di Unity.

- [How to maximize AR and VR performance with advanced stereo rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) (Come ottimizzare le prestazioni di AR e VR con il rendering stereo avanzato)
- [Single Pass Instancing](https://docs.unity3d.com/Manual/SinglePassInstancing.html) (Creazione di istanze a singolo passaggio)

>[!NOTE]
> Un problema comune relativo al rendering con istanze a singolo passaggio si verifica se gli sviluppatori dispongono già di shader personalizzati non scritti per la creazione di istanze. Dopo l'abilitazione di questa funzionalità, gli sviluppatori possono notare che per alcuni GameObject viene eseguito il rendering in un solo occhio. Ciò è dovuto al fatto che gli shader personalizzati associati non hanno le proprietà appropriate per la creazione di istanze.
>
> Per informazioni su come risolvere questo problema, vedi l'articolo di Unity [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) (Rendering stereo a singolo passaggio per HoloLens)

### <a name="enable-depth-buffer-sharing"></a>Abilitare la condivisione del buffer di profondità

Per ottenere una migliore stabilità dell'ologramma dalla percezione dell'utente, è consigliabile abilitare la proprietà **Depth Buffer Sharing** in Unity. Attivando questa opzione, Unity condividerà la mappa di profondità prodotta dall'applicazione con Windows Mixed Reality piattaforma. La piattaforma può quindi ottimizzare meglio la stabilità degli ologrammi in modo specifico per la scena per qualsiasi fotogramma sottoposto a rendering dall'applicazione.

Per abilitare questa funzionalità nel tuo progetto Unity

1) Apri **Player XR Settings** (Impostazioni XR riproduttore). A tale scopo, vai a **Edit** (Modifica) > **Project Settings** (Impostazioni progetto) > **Player** (Riproduttore) > **XR Settings** (Impostazioni XR)
2) Selezionare la casella di controllo **Enable Depth Buffer Sharing** (Abilita condivisione buffer di profondità) in Virtual Reality **SDKs**  >  **Windows Mixed Reality** expansion (Virtual **Reality Supported(** Realtà virtuale supportata)

È anche consigliabile selezionare profondità **a 16 bit** sotto l'impostazione **Formato** profondità in questo pannello, in particolare per lo sviluppo di HoloLens. La selezione di 16 bit rispetto a 24 bit ridurrà significativamente i requisiti di larghezza di banda, in quanto sarà necessario spostare/elaborare meno dati.

Perché la piattaforma Windows Mixed Reality ottimizzare la stabilità degli ologrammi, si basa sul buffer di profondità per essere accurato e corrispondere a qualsiasi ologramma sottoposto a rendering sullo schermo. Pertanto, con la condivisione del buffer di profondità, è importante quando si esegue il rendering del colore, per eseguire anche il rendering della profondità. In Unity la maggior parte dei materiali Opaque o TransparentCutout eseguirà il rendering della profondità per impostazione predefinita, ma gli oggetti trasparenti e di testo non eseguiranno il rendering della profondità anche se dipendente dallo shader e così via.

Se si usa lo [shader Mixed Reality Toolkit Standard,](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)per eseguire il rendering della profondità per gli oggetti trasparenti:

1) Selezionare il materiale trasparente che usa lo shader MRTK Standard e aprire la finestra dell'editor inspector
2) Selezionare il **pulsante Correggi ora** all'interno dell'avviso di condivisione del buffer di profondità. Questa operazione può essere eseguita anche manualmente impostando modalità **di rendering** su **Personalizzato.** quindi impostare **Mode (Modalità)** **su Transparent** (Trasparente) e infine Depth **Write (Scrittura profondità)** su **On (Attivata)**

> [!IMPORTANT]
> Gli sviluppatori devono fare attenzione agli Z-fighting quando modificano questi valori insieme alle impostazioni del piano vicino/lontano della fotocamera. Z-Fighting si verifica quando due gameobject tentano di eseguire il rendering allo stesso pixel e a causa di limitazioni nella fedeltà del buffer di profondità (ad esempio z depth), Unity non è in grado di distinguere quale oggetto si trova davanti all'altro. Gli sviluppatori noteranno uno sfarfallio tra due oggetti gioco mentre *si distondono* per lo stesso valore di profondità z. Questo problema può essere risolto passando al formato di profondità a 24 bit perché sarà presente un intervallo più ampio di valori su cui calcolare ogni oggetto per la profondità z dalla fotocamera.
>
> Tuttavia, è consigliabile, in particolare per lo sviluppo di HoloLens, modificare i piani vicini e di lontano della fotocamera in un intervallo più piccolo e mantenere invece il formato di profondità a 16 bit. La profondità z viene mappata in modo non lineare all'intervallo di valori lungo i piani della fotocamera vicino e lontano. È possibile modificare questa  impostazione selezionando la fotocamera principale nella scena e in **Inspector**(Controllo) modificare i valori near **& Far Clipping Plane** (Piano di ritaglio da vicino) per ridurne l'intervallo (ad esempio da 1000 m a 100m o altro valore x e così via.

>[!IMPORTANT]
> [Unity non crea un buffer degli stencil quando](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) si usa il formato di profondità a 16 bit. Di conseguenza, alcuni effetti dell'interfaccia utente di Unity e altri effetti necessari per gli stencil non funzionano a meno che non sia selezionato un formato di profondità a 24 bit che creerà un buffer degli stencil a [8 bit.](https://docs.unity3d.com/Manual/SL-Stencil.html)

### <a name="building-for-il2cpp"></a>Compilazione per IL2CPP

Unity ha deprecato il supporto per il back-end di scripting .NET e pertanto consiglia agli sviluppatori di usare **IL2CPP** per le build UWP di Visual Studio. Anche se ciò offre vari vantaggi, la creazione di una soluzione di Visual Studio da Unity per **IL2CPP** può essere più lenta rispetto al metodo .NET precedente. È quindi consigliabile seguire le procedure consigliate per la creazione di **IL2CPP** per risparmiare tempo di iterazione dello sviluppo.

1) Sfruttare la compilazione incrementale compilando ogni volta il progetto nella stessa directory, riutilizzando i file predefiniti
2) Disabilitare le analisi del software antimalware per il progetto & di compilazione
   - Aprire **Virus & protezione dalle minacce nell'app** impostazioni Windows 10 sicurezza
   - Selezionare **Manage Settings (Gestisci** impostazioni) in Virus & threat protection settings **(Impostazioni di protezione dalle minacce da virus)**
   - Selezionare **Aggiungi o rimuovi esclusioni** nella sezione **Esclusioni**
   - Selezionare **Add an exclusion (Aggiungi un'esclusione)** e selezionare la cartella contenente il codice del progetto Unity e gli output di compilazione
3) Usare un'SSD per la compilazione

Per [altre informazioni, vedere Ottimizzazione dei tempi di compilazione per IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)

> [!NOTE]
> Inoltre, potrebbe essere utile configurare un [server di cache](https://docs.unity3d.com/Manual/CacheServer.html), soprattutto per i progetti Unity con una grande quantità di asset (esclusi i file di script) o con asset/scene in continua evoluzione. All'apertura di un progetto, Unity archivia gli asset validi in un formato della cache interna nel computer di sviluppo. Gli elementi devono essere reimportati e quindi rielaborati in caso di modifica. Questo processo può essere eseguito una volta, salvato in un server di cache e quindi condiviso con altri sviluppatori in modo da risparmiare tempo, evitando a ciascuno sviluppatore di elaborare la reimportazione di nuove modifiche in locale.

## <a name="publishing-properties"></a>Proprietà di pubblicazione

### <a name="holographic-splash-screen"></a>Schermata iniziale olografica

HoloLens ha una CPU e una GPU di classe mobile, il che significa che il caricamento delle app potrebbe richiedere un po' più tempo. Durante il caricamento dell'app, gli utenti vedono solo il nero e quindi si chiederanno cosa succede. Per rasurirli durante il caricamento, è possibile aggiungere una schermata iniziale olografica.

Per attivare o disattivare la schermata iniziale olografica:

1) Passare alla **pagina Edit** Project Settings Player  >  **(Modifica**  >  **lettore impostazioni** progetto)
2) Selezionare la **scheda Windows Store** e aprire la sezione **Immagine** iniziale
3) Applica l'immagine nella **proprietà Windows Holographic > Holographic Splash Image** (Immagine iniziale olografica).
    - Attivando o disattivando **l'opzione Show Unity Splash Screen** (Mostra schermata iniziale unity) verrà abilitata o disabilitata la schermata iniziale con marchio Unity. Se non si ha una licenza Unity Pro, verrà sempre visualizzata la schermata iniziale con marchio Unity.
    - Se viene **applicata un'immagine** iniziale olografica, verrà sempre visualizzata se la casella di controllo Show Unity Splash Screen (Mostra schermata iniziale Unity) è abilitata o disabilitata. La specifica di un'immagine iniziale olografica personalizzata è disponibile solo per gli sviluppatori con una licenza Unity Pro.

|  Visualizzare la schermata iniziale di Unity  |  Immagine iniziale olografica  |  Comportamento |
|----------|----------|----------|
|  On  |  Nessuno  |  Mostra la schermata iniziale predefinita di Unity per 5 secondi o fino a quando l'app non viene caricata, a seconda del valore più lungo. |
|  On  |  Personalizzato  |  Mostra la schermata iniziale personalizzata per 5 secondi o fino a quando l'app non viene caricata, a seconda del valore più lungo. |
|  Off  |  Nessuno  |  Mostra il nero trasparente (nulla) fino a quando l'app non viene caricata. |
|  Off  |  Personalizzato  |  Mostra la schermata iniziale personalizzata per 5 secondi o fino a quando l'app non viene caricata, a seconda del valore più lungo. |

Per [altre informazioni, vedere la documentazione](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) della schermata iniziale di Unity.

### <a name="tracking-loss"></a>Perdita del tracciamento

Un visore VR di realtà mista dipende dalla visualizzazione dell'ambiente che lo circonda per costruire sistemi di [coordinate](coordinate-systems-in-unity.md)bloccati a livello mondiale, che consentono agli ologrammi di rimanere in posizione. Quando il visore VR non riesce a individuarsi nel mondo, si dice che il visore VR ha perso *il tracciamento.* In questi casi, le funzionalità che dipendono dai sistemi di coordinate bloccati a livello mondiale, ad esempio le fasi spaziali, gli ancoraggi nello spazio e il mapping spaziale, non funzionano.

Se si verifica una perdita di rilevamento, il comportamento predefinito di [](https://docs.unity3d.com/Manual/ExecutionOrder.html)Unity è interrompere il rendering degli ologrammi, sospendere il ciclo del gioco e visualizzare una notifica di rilevamento persa che segue lo sguardo fisso degli utenti. Le notifiche personalizzate possono essere fornite anche sotto forma di un'immagine di perdita di rilevamento. Per le app che dipendono dal rilevamento per l'intera esperienza, è sufficiente consentire a Unity di gestirla completamente fino a quando il rilevamento non viene recuperato. Gli sviluppatori possono fornire un'immagine personalizzata da visualizzare durante la perdita di rilevamento.

Per personalizzare l'immagine di rilevamento della perdita:

1) Passare alla **pagina Edit** Project Settings Player  >  **(Modifica**  >  **lettore impostazioni** progetto)
2) Selezionare la scheda **Windows Store** e aprire la **sezione Immagine** iniziale
3) Applica l'immagine nella proprietà **Windows Holographic > Tracking Loss Image** ( Immagine perdita di tracciamento).

#### <a name="opt-out-of-automatic-pause"></a>Rifiutare esplicitamente la sospensione automatica

Alcune app potrebbero non richiedere il [](coordinate-systems-in-unity.md) rilevamento ,ad esempio app solo per l'orientamento, ad esempio visualizzatori video a 360 gradi, o potrebbero dover continuare a elaborare senza interruzioni mentre il rilevamento viene perso. È possibile rifiutare esplicitamente la perdita predefinita del comportamento di rilevamento, ma si è responsabili della disattivazione o della disattivazione di tutti gli oggetti, che non vengono eseguono correttamente il rendering in uno scenario di perdita di rilevamento. Nella maggior parte dei casi, l'unico contenuto di cui è consigliabile eseguire il rendering in questo caso è il contenuto bloccato dal corpo, centrato intorno alla fotocamera principale.

Per rifiutare esplicitamente il comportamento di sospensione automatica:

1) Passare alla pagina **Edit** Project Settings Player  >  **(Modifica**  >  **lettore impostazioni progetto)**
2) Selezionare la **scheda Windows Store** e aprire la sezione **Immagine** iniziale
3) Modificare le **caselle di controllo Windows Holographic > On Tracking Loss Pause e Show Image.**

#### <a name="tracking-loss-events"></a>Tenere traccia degli eventi di perdita

Per definire il comportamento personalizzato quando il rilevamento viene perso, gestire gli eventi di [perdita di rilevamento globali](tracking-loss-in-unity.md).

### <a name="capabilities"></a>Funzionalità

Per poter sfruttare determinate funzionalità, un'app deve dichiarare le funzionalità appropriate nel manifesto. Le dichiarazioni del manifesto possono essere effettuate in Unity in modo che siano incluse in ogni esportazione futura del progetto.

Le funzionalità possono essere abilitate per un'applicazione di realtà mista:

1) Passare alla **pagina Edit** Project Settings Player  >  **(Modifica**  >  **lettore impostazioni** progetto)
2) Selezionare la **scheda Windows Store,** aprire la **sezione Impostazioni di** pubblicazione e cercare l'elenco **Funzionalità**

Le funzionalità applicabili per abilitare le API di uso comune per le app Holographic sono:
<br>

|  Funzionalità  |  API che richiedono funzionalità |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  Webcam  |  PhotoCapture e VideoCapture |
|  PicturesLibrary/VideosLibrary  |  PhotoCapture o VideoCapture, rispettivamente (quando si archivia il contenuto acquisito) |
|  Microfono  |  VideoCapture (durante l'acquisizione di audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (e per usare il profiler Unity) |

## <a name="see-also"></a>Vedi anche

* [Panoramica dello sviluppo per Unity](unity-development-overview.md)
* [Informazioni sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)