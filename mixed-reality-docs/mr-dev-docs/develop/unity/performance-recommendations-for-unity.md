---
title: Consigli sulle prestazioni per Unity
description: Informazioni sui suggerimenti specifici per Unity per migliorare le prestazioni con le impostazioni di progetto, la profilazione, la gestione della memoria nelle app di realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2019
ms.topic: article
keywords: grafica, cpu, gpu, rendering, garbage collection, hololens
ms.localizationpriority: high
ms.openlocfilehash: f8757e5a5f5c9163dc70d8c8d0e93848c49a6694
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "101759727"
---
# <a name="performance-recommendations-for-unity"></a>Consigli sulle prestazioni per Unity

Questo articolo si basa sulle [raccomandazioni sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), ma si sofferma sui miglioramenti specifici di Unity.

## <a name="use-recommended-unity-project-settings"></a>Usare le impostazioni consigliate per il progetto Unity

Il primo passaggio più importante per l'ottimizzazione delle prestazioni delle app di realtà mista in Unity è assicurarsi di usare le [impostazioni di ambiente consigliate per Unity](recommended-settings-for-unity.md). Questo articolo include contenuto con alcune delle configurazioni scena più importanti per la creazione di app di realtà mista ad alte prestazioni. Alcune di queste impostazioni consigliate sono poste in evidenza anche di seguito.

## <a name="how-to-profile-with-unity"></a>Come eseguire la profilatura con Unity

Unity fornisce un **[profiler](https://docs.unity3d.com/Manual/Profiler.html)** incorporato, che si rivela un'ottima risorsa per raccogliere importanti informazioni sulle prestazioni per la tua app specifica. Benché sia possibile eseguire il profiler nell'editor, queste metriche non rappresentano il vero ambiente di runtime e i risultati devono quindi essere usati con cautela. Per ottenere le informazioni più accurate e utilizzabili possibili, è consigliabile profilare in remoto l'applicazione mentre è in esecuzione nel dispositivo. Inoltre, anche [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) di Unity è uno strumento di analisi molto potente da usare.

Unity fornisce documentazione esauriente sugli argomenti seguenti:
1) Come connettere il [profiler Unity alle applicazioni UWP in remoto](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Come [diagnosticare i problemi di prestazioni con il profiler Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window) in modo efficace

>[!NOTE]
> Con il profiler Unity connesso, e dopo aver aggiunto il profiler GPU (vedi *Add Profiler* (Aggiungi profiler) nell'angolo superiore destro), è possibile controllare nel profiler quanto tempo della CPU e della GPU viene impiegato. Ciò consente allo sviluppatore di ottenere una rapida approssimazione se l'applicazione è associata alla CPU o alla GPU.
>
> ![CPU Unity e GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Consigli sulle prestazioni della CPU

Il contenuto seguente illustra più in dettaglio le procedure per migliorare le prestazioni, soprattutto per lo sviluppo in C# e Unity.

#### <a name="cache-references"></a>Memorizzare nella cache i riferimenti

È consigliabile memorizzare nella cache i riferimenti a tutti i componenti e GameObject pertinenti in fase di inizializzazione perché le chiamate di funzione ripetute, ad esempio *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* e [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html), sono più dispendiose rispetto al costo della memoria per l'archiviazione di un puntatore. . *Camera.main* usa solo *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* sotto, che con costi elevati cerca nel grafico della scena un oggetto fotocamera con il tag *"MainCamera"* .

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> Evitare GetComponent(stringa) <br/>
> Quando usi *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , si verificano overload diversi. È importante usare sempre le implementazioni basate sul tipo e mai l'overload di ricerca basato su una stringa. La ricerca per stringa nella scena è notevolmente più costosa rispetto alla ricerca per tipo. <br/>
> (Utilizzabile) Component GetComponent(Type tipo) <br/>
> (Utilizzabile) T GetComponent\<T>() <br/>
> (Da evitare) Component GetComponent(stringa)> <br/>

#### <a name="avoid-expensive-operations"></a>Evitare operazioni costose

1) **Evitare l'uso di [LINQ](/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Benché LINQ possa essere pulito e facile da leggere e scrivere, richiede in genere capacità di calcolo e memoria superiori rispetto alla scrittura manuale dell'algoritmo.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **API Unity comuni**

    Alcune API Unity, benché utili, possono dare luogo a elevati costi di esecuzione. La maggior parte di esse comporta la ricerca di un elenco corrispondente di GameObject nell'intero grafico della scena. Queste operazioni possono in genere essere evitate memorizzando nella cache i riferimenti o implementando un componente di gestione per i GameObject per tenere traccia dei riferimenti in fase di runtime.

    ```csharp
        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()
    ```

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* e *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* devono essere eliminate in ogni modo. Queste funzioni possono essere 1.000 volte più lente rispetto alle chiamate di funzioni dirette.

3) **Attenzione alla conversione boxing**

    La [conversione boxing](/dotnet/csharp/programming-guide/types/boxing-and-unboxing) è un concetto base del linguaggio e del runtime C#. Si tratta del processo di wrapping delle variabili di tipo valore come `char`, `int`, `bool` e così via in variabili di tipo riferimento. Quando una variabile di tipo valore viene "sottoposta alla conversione boxing", viene incapsulata in un elemento `System.Object` archiviato nell'heap gestito. La memoria viene allocata e alla fine, quando viene eliminata, deve essere elaborata dal Garbage Collector. Queste allocazioni e deallocazioni comportano un costo in termini di prestazioni e in molti scenari non sono necessarie o possono essere facilmente sostituite da un'alternativa meno dispendiosa.

    Per evitare la conversione boxing, assicurarsi che le variabili, i campi e le proprietà in cui vengono archiviati i tipi numerici e gli struct (inclusi `Nullable<T>`) siano fortemente tipizzati come tipi specifici, ad esempio `int`, `float?` o `MyStruct`, anziché usare l'oggetto.  Se si inseriscono questi oggetti in un elenco, usare un elenco fortemente tipizzato, ad esempio `List<int>`, invece che `List<object>` o `ArrayList`.

    **Esempio di conversione boxing in C#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

#### <a name="repeating-code-paths"></a>Percorsi di codice ripetuti

Le eventuali funzioni di callback Unity ripetute (ovvero Update) eseguite più volte al secondo e/o ogni frame devono essere scritte con la massima attenzione. Tutte le operazioni dispendiose in questo caso avranno un effetto notevole e coerente sulle prestazioni.

1) **Funzioni di callback vuote**

    Nonostante il codice seguente possa sembrare innocuo se lasciato nell'applicazione, soprattutto perché ogni script di Unity viene inizializzato automaticamente con un metodo Update, questi callback vuoti possono diventare dispendiosi. Unity opera alternandosi tra un limite di codice non gestito e uno gestito, tra il codice di UnityEngine e il codice dell'applicazione. Il cambio di contesto su questo bridge è piuttosto dispendioso, anche se non sono presenti elementi da eseguire. Lo scenario diventa particolarmente problematico se l'app include centinaia di GameObject con componenti che hanno callback di Unity ripetuti vuoti.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update() è la manifestazione più comune di questo problema di prestazioni, ma altri callback Unity ripetuti, come quelli riportati di seguito, possono essere ugualmente problematici, se non addirittura peggiori: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage() e così via. 

2) **Operazioni per favorire un'unica esecuzione per frame**

    Le API Unity seguenti sono operazioni comuni per molte app olografiche. Benché non sia sempre possibile, i risultati di queste funzioni possono in genere essere calcolati una sola volta e riutilizzati nell'applicazione per un determinato frame.

    a) È opportuno avere una classe singleton o un servizio dedicato per gestire l'operazione Raycast dello sguardo fisso nella scena e quindi riutilizzare questo risultato in tutti gli altri componenti della scena, invece di avere operazioni Raycast ripetute e identiche eseguite da ogni componente. Alcune applicazioni possono richiedere Raycast da origini diverse o a fronte di [LayerMask](https://docs.unity3d.com/ScriptReference/LayerMask.html) differenti.
    
    ```csharp
        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()
    ```

    b) Evitare operazioni GetComponent() in callback Unity ripetuti come Update() [memorizzando nella cache i riferimenti](#cache-references) in Start() o Awake()
    
    ```csharp
        UnityEngine.Object.GetComponent()
    ```

    c) È consigliabile creare un'istanza di tutti gli oggetti, se possibile, in fase di inizializzazione e usare il [pooling di oggetti](#object-pooling) per riciclare e riutilizzare GameObject durante il runtime dell'applicazione

    ```csharp
        UnityEngine.Object.Instantiate()
    ```

3) **Evitare le interfacce e i costrutti virtuali**

    Richiamando le chiamate di funzione tramite interfacce anziché tramite oggetti diretti o chiamando le funzioni virtuali può spesso essere molto più dispendioso che non usare costrutti diretti o chiamate di funzione dirette. Se l'interfaccia o la funzione virtuale non è necessaria, deve essere rimossa. Tuttavia, il calo di prestazioni causato dall'uso di questi approcci viene compensato dai vantaggi ottenuti dal punto di vista della semplificazione della collaborazione in fase di sviluppo, della leggibilità e della gestibilità del codice.

    In genere, è consigliabile non contrassegnare campi e funzioni come virtuali, a meno che non si preveda chiaramente che il membro in questione debba essere sovrascritto. È necessario prestare particolare attenzione ai percorsi di codice ad alta frequenza che vengono chiamati numerose volte per fotogramma o anche una sola volta per fotogramma, ad esempio come nel caso di un metodo `UpdateUI()`.

4) **Evitare il passaggio di struct in base al valore**

    Diversamente dalle classi, gli struct sono tipi valore e, quando vengono passati direttamente a una funzione, il relativo contenuto viene copiato in un'istanza appena creata. Questa copia comporta altri costi in termini di CPU, oltre che di memoria aggiuntiva nello stack. Per gli struct di piccole dimensioni, l'effetto è minimo e quindi accettabile. Tuttavia, per le funzioni richiamate ripetutamente a ogni frame e per le funzioni che accettano struct di grandi dimensioni, se possibile, modifica la definizione della funzione in modo che il passaggio avvenga per riferimento. [Per altre informazioni, vedi qui](/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Varie

1) **Fisica**

    a) In genere, il modo più semplice per migliorare la fisica consiste nel limitare la quantità di tempo impiegata per la fisica o il numero di iterazioni al secondo. Questa operazione ridurrà la precisione della simulazione. Vedi [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity

    b) I tipi di collider in Unity presentano caratteristiche di prestazioni estremamente diverse. Procedendo da sinistra verso destra, i collisori riportati di seguito vanno da quelli che garantiscono le prestazioni migliori a quelli che forniscono le prestazioni peggiori. È importante evitare i collider di tipo Mesh, che sono molto più dispendiosi rispetto ai collider primitivi.

    Sfera < Capsula < Casella <<< Mesh (convessa) < Mesh (non convessa)

    Per altre informazioni, vedi [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) (Procedure consigliate per la fisica in Unity)

2) **Animazioni**

    Disabilita le animazioni inattive disabilitando il componente Animator (Animatore); la disabilitazione dell'oggetto gioco non avrà lo stesso effetto. Evita i modelli di progettazione in cui un animatore si trova in un ciclo che imposta un valore sullo stesso elemento. Per questa tecnica si verifica un notevole overhead, senza alcun effetto sull'applicazione. [Per altre informazioni, vedi qui.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmi complessi**

    Se l'applicazione usa algoritmi complessi, ad esempio per cinematica inversa, ricerca di percorsi e così via, cerca un approccio più semplice o modifica le impostazioni pertinenti per le relative prestazioni

## <a name="cpu-to-gpu-performance-recommendations"></a>Consigli sulle prestazioni della CPU in relazione alla GPU

In genere, le prestazioni della CPU in relazione alla GPU si basano sulle **chiamate di disegno** inviate alla scheda grafica. Per migliorare le prestazioni, tali chiamate devono essere strategicamente **a) ridotte** o **b) ristrutturate** per risultati ottimali. Poiché le chiamate di disegno di per sé sono a elevato utilizzo di risorse, la loro riduzione comporterà una riduzione del lavoro complessivo richiesto. Inoltre, i cambiamenti di stato tra una chiamata di disegno e l'altra richiedono costose operazioni di convalida e conversione nel driver di grafica. Pertanto, la ristrutturazione delle chiamate di disegno dell'applicazione per limitare i cambiamenti di stato (ad esempio, il passaggio da un materiale all'altro e così via) può migliorare le prestazioni.

Unity offre un interessante articolo che fornisce una panoramica sull'invio delle chiamate di disegno in batch per la propria piattaforma.
- [Unity Draw Call Batching](https://docs.unity3d.com/Manual/DrawCallBatching.html) (Invio delle chiamate di disegno in batch in Unity)

#### <a name="single-pass-instanced-rendering"></a>Rendering con istanze a singolo passaggio

Il rendering con istanze a singolo passaggio in Unity consente di ridurre le chiamate di disegno per ogni occhio a un'unica chiamata di disegno con istanza. A causa della coerenza della cache tra due chiamate di disegno, si verifica anche un certo miglioramento delle prestazioni per la GPU.

Per abilitare questa funzionalità nel tuo progetto Unity
1)  Apri **Player XR Settings** (Impostazioni XR riproduttore). A tale scopo, vai a **Edit** (Modifica) > **Project Settings** (Impostazioni progetto) > **Player** (Riproduttore) > **XR Settings** (Impostazioni XR)
2) Scegli **Single Pass Instanced** (Con istanze a singolo passaggio) dal menu a discesa **Stereo Rendering Method** (Metodo di rendering stereo). Deve essere selezionata la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata)

Per i dettagli su questo approccio di rendering, leggi gli articoli seguenti.
- [How to maximize AR and VR performance with advanced stereo rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) (Come ottimizzare le prestazioni di AR e VR con il rendering stereo avanzato)
- [Single Pass Instancing](https://docs.unity3d.com/Manual/SinglePassInstancing.html) (Creazione di istanze a singolo passaggio) 

>[!NOTE]
> Un problema comune relativo al rendering con istanze a singolo passaggio si verifica se gli sviluppatori dispongono già di shader personalizzati non scritti per la creazione di istanze. Dopo l'abilitazione di questa funzionalità, gli sviluppatori possono notare che per alcuni GameObject viene eseguito il rendering in un solo occhio. Ciò è dovuto al fatto che gli shader personalizzati associati non hanno le proprietà appropriate per la creazione di istanze.
>
> Per informazioni su come risolvere questo problema, vedi l'articolo di Unity [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) (Rendering stereo a singolo passaggio per HoloLens)

#### <a name="static-batching"></a>Invio in batch statico

Unity è in grado di inviare in batch numerosi oggetti statici per ridurre le chiamate di disegno alla GPU. L'invio in batch statico funziona per la maggior degli oggetti [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) in Unity che **1) condividono lo stesso materiale** e **2) sono tutti contrassegnati come *Static*** (selezionare un oggetto in Unity e quindi la casella di controllo nell'angolo superiore destro della finestra Inspector (Controllo)). I GameObject contrassegnati come *statici* non possono essere spostati per l'intero runtime dell'applicazione. Può risultare pertanto difficile sfruttare l'invio in batch statico su HoloLens, dove virtualmente tutti gli oggetti devono essere posizionati, spostati, ridimensionati e così via. Per i visori VR immersive, l'invio in batch statico può ridurre in modo significativo le chiamate di disegno e quindi migliorare le prestazioni.

Per altri dettagli, leggi *Static Batching* (Invio in batch statico) in [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) (Invio di chiamate di disegno in batch in Unity).

#### <a name="dynamic-batching"></a>Invio in batch dinamico

Poiché è problematico contrassegnare gli oggetti come *Static* per lo sviluppo per HoloLens, l'invio in batch dinamico può essere un'ottima soluzione per compensare la mancanza di questa funzionalità. Può essere utile anche nei visori VR immersive. Può tuttavia essere difficile abilitare l'invio in batch dinamico in Unity perché i GameObject devono **a) condividere lo stesso materiale** e **b) soddisfare un lungo elenco di altri criteri**.

Per l'elenco completo, leggi *Dynamic Batching* (Invio in batch dinamico) in [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) (Invio di chiamate di disegno in batch in Unity). In genere, i GameObject diventano non validi per l'invio in batch dinamico perché i dati di mesh associati non possono essere più di 300 vertici.

#### <a name="other-techniques"></a>Altre tecniche

L'invio in batch può avere luogo solo se più GameObject sono in grado di condividere lo stesso materiale. Questa operazione generalmente verrà impedita dal fatto che i GameObject devono avere una trama univoca per il rispettivo materiale. È pratica comune combinare le trame in un'unica grande trama, in base a un metodo denominato [creazione di fogli di sprite](https://en.wikipedia.org/wiki/Texture_atlas).

Inoltre, è preferibile combinare le mesh in un unico GameObject, ove possibile e ragionevole. Ogni renderer in Unity avrà associate le proprie chiamate di disegno rispetto all'invio di una mesh combinata facente capo a un solo renderer.

>[!NOTE]
> Se si modificano le proprietà di Renderer.material in fase di runtime, verrà creata una copia del materiale e, di conseguenza, potenzialmente si interromperà il batch. Usa Renderer.sharedMaterial per modificare le proprietà di materiale condivise tra GameObject.

## <a name="gpu-performance-recommendations"></a>Consigli sulle prestazioni della GPU

Scopri di più sull'[ottimizzazione del rendering della grafica in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>Ottimizzare la condivisione buffer di intensità

È consigliabile abilitare **Depth buffer sharing** (Condivisione buffer di intensità) in **Player XR Settings** (Impostazioni XR riproduttore) ai fini dell'ottimizzazione per la [stabilità degli ologrammi](../platform-capabilities-and-apis/Hologram-stability.md). Se però con questa impostazione viene abilitata la riproiezione in fase avanzata basata sull'intensità, è opportuno selezionare **16-bit depth format** (Formato con intensità a 16 bit) anziché **24-bit depth format** (Formato con intensità a 24 bit). I buffer di intensità a 16 bit ridurranno in modo significativo la larghezza di banda (e quindi la potenza) associata al traffico di buffer di intensità. Questo può essere un ottimo risultato sia in termini di riduzione della potenza che di miglioramento delle prestazioni. Tuttavia, quando viene usata l'impostazione *16-bit depth format* (Formato con intensità a 16 bit), sono possibili due risultati negativi.

**Z-fighting**

La fedeltà dell'intervallo di intensità inferiore rende più probabile il verificarsi dell'effetto [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) con 16 bit che con 24 bit. Per evitare questi artefatti, modifica i piani di ritaglio vicini/lontani della [camera Unity](https://docs.unity3d.com/Manual/class-Camera.html) in modo da tenere conto della minore precisione. Per le applicazioni basate su HoloLens, un piano di ritaglio lontano di 50 m al posto dei 1000 m predefiniti di Unity, consente in genere di eliminare l'effetto z-fighting.

**Buffer degli stencil disabilitato**

Quando Unity crea una [trama di rendering con intensità a 16 bit](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), non viene creato alcun buffer degli stencil. Se si seleziona 24-bit depth format (Formato con intensità a 24 bit), come indicato nella documentazione di Unity, verrà creato un buffer z a 24 bit, insieme a un [buffer degli stencil a 8 bit] (https://docs.unity3d.com/Manual/SL-Stencil.html) (se i 32 bit sono applicabili su un dispositivo, com'è in genere il caso su HoloLens).

### <a name="avoid-full-screen-effects"></a>Evitare effetti a schermo intero

Le tecniche che agiscono sullo schermo intero possono essere dispendiose perché il loro ordine di grandezza è di milioni di operazioni ogni frame. È consigliabile evitare [effetti di post-elaborazione](https://docs.unity3d.com/Manual/PostProcessingOverview.html), ad esempio l'anti-aliasing, l'effetto bloom e altro ancora.

### <a name="optimal-lighting-settings"></a>Impostazioni ottimali dell'illuminazione

La funzionalità [Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) (Illuminazione globale in tempo reale) in Unity può fornire risultati visivi sorprendenti, ma comporta pesanti calcoli per l'illuminazione. È consigliabile disabilitare questa funzionalità per ogni file di scena di Unity tramite **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination** (Finestra > Rendering > Impostazioni illuminazione > Deseleziona Illuminazione globale in tempo reale).

È inoltre consigliabile disabilitare tutte le ombreggiature perché anche queste aggiungono passaggi di GPU dispendiosi nella scena di Unity. Le ombreggiature possono essere disabilitate per la singola luce, ma possono anche essere controllate in modo olistico tramite le impostazioni relative alla qualità.

**Edit** (Modifica)  > **Project Settings** (Impostazioni progetto) e quindi seleziona la categoria **Quality** (Qualità) > Seleziona **Low Quality** (Qualità bassa) per la piattaforma UWP. È anche sufficiente impostare la proprietà **Shadows** (Ombreggiature) su **Disable Shadows** (Disabilita ombreggiature).

È consigliabile usare l'illuminazione con baking con i modelli in Unity.

### <a name="reduce-poly-count"></a>Ridurre il numero dei poligoni

Il numero di poligoni viene ridotto tramite
1) Rimozione di oggetti da una scena
2) Decimazione degli asset, che riduce il numero di poligoni per una determinata mesh
3) Implementazione nell'applicazione di un [sistema LOD (Level of Detail)](https://docs.unity3d.com/Manual/LevelOfDetail.html) che esegue il rendering di oggetti lontani con una versione costituita da meno poligoni della stessa geometria

### <a name="understanding-shaders-in-unity"></a>Informazioni sugli shader in Unity

Una semplice approssimazione per confrontare gli shader in termini di prestazioni consiste nell'identificare il numero medio di operazioni eseguite da ognuno di essi in fase di runtime. Questa attività può essere effettuata facilmente in Unity.

1) Selezionare l'asset dello shader oppure selezionare un materiale e quindi nell'angolo superiore destro della finestra Inspector (Controllo) fare clic sull'icona a forma di ingranaggio e su **"Select Shader"** (Seleziona shader)

    ![Selezione dello shader in Unity](images/Select-shader-unity.png)
2) Con l'asset dello shader selezionato, fare clic sul pulsante **"Compile and show code"** (Compila e mostra il codice) nella finestra Inspector (Controllo)

    ![Compilazione del codice dello shader in Unity](images/compile-shader-code-unity.PNG)

3) Dopo la compilazione, cerca nei risultati la sezione delle statistiche con il numero di diverse operazioni per il vertex shader e per il pixel shader (Nota: i pixel shader spesso vengono indicati anche come shader di frammento)

    ![Operazioni degli shader standard di Unity](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>Ottimizzare i pixel shader

Esaminando i risultati statistici compilati con il metodo sopra descritto, lo [ shader di frammento](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) eseguirà in genere più operazioni rispetto al [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) in media. Lo shader di frammento (noto anche come pixel shader) viene eseguito per pixel nell'output su schermo, mentre il vertex shader viene eseguito solo per vertice di tutte le mesh disegnate sullo schermo. 

Pertanto, oltre ad avere più istruzioni rispetto ai vertex shader a causa di tutti i calcoli per l'illuminazione, gli shader di frammento vengono quasi sempre eseguiti su un set di dati più grande. Ad esempio, se l'output su schermo è un'immagine 2 K per 2 K, lo shader di frammento può venire eseguito 2000*2000 = 4 milioni di volte. Se viene eseguito il rendering di due occhi, questo numero raddoppia perché le schermate sono due. Se un'applicazione di realtà mista prevede più passaggi, effetti di post-elaborazione a schermo intero o il rendering di più mesh sullo stesso pixel, questo numero aumenterà in modo considerevole. 

Perciò, la riduzione del numero di operazioni nello shader di frammento può in genere assicurare un miglioramento delle prestazioni notevolmente superiore rispetto alle ottimizzazioni nel vertex shader.

#### <a name="unity-standard-shader-alternatives"></a>Alternative agli shader standard di Unity

Invece di usare un rendering fisico (PBR, Physically Based Rendering) o un altro shader di alta qualità, cerca di usare uno shader più efficiente e più economico. [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) offre lo [shader standard MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mrtk-standard-shader.md) che è stato ottimizzato per i progetti di realtà mista.

Unity offre anche shader senza illuminazione, con illuminazione dei vertici, diffusi e altre opzioni di shader semplificate che sono molto più veloci rispetto allo shader standard di Unity. Per informazioni più dettagliate, vedi [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) (Utilizzo e prestazioni degli shader incorporati).

#### <a name="shader-preloading"></a>Precaricamento degli shader

Usa il *precaricamento dello shader* e altri trucchi per ottimizzare il [tempo di caricamento degli shader](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html). In particolare, con il precaricamento non si verificheranno problemi di blocco dovuti alla compilazione dello shader in fase di runtime.

### <a name="limit-overdraw"></a>Limitare le sovrapposizioni

In Unity è possibile visualizzare le sovrapposizioni per la scena attivando il [**menu della modalità di disegno**](https://docs.unity3d.com/Manual/ViewModes.html) nell'angolo superiore sinistro della **vista Scene** (Scena) e scegliendo **Overdraw** (Sovrapposizione).

In genere, è possibile ridurre le sovrapposizioni eseguendo il culling degli oggetti prima che vengano inviati alla GPU. Unity fornisce i dettagli sull'implementazione del [culling di occlusione](https://docs.unity3d.com/Manual/OcclusionCulling.html) per il proprio motore.

## <a name="memory-recommendations"></a>Consigli sulla memoria

Un numero eccessivo di operazioni di allocazione e deallocazione può avere effetti negativi sull'applicazione olografica, causando prestazioni non coerenti, frame bloccati e altri comportamenti indesiderati. È particolarmente importante comprendere le considerazioni relative alla memoria durante le attività di sviluppo in Unity perché la gestione della memoria è controllata dal Garbage Collector.

#### <a name="garbage-collection"></a>Garbage Collection

Le app olografiche perderanno il tempo di calcolo dell'elaborazione per il Garbage Collector (GC) quando questo viene attivato per analizzare gli oggetti non più compresi nell'ambito durante l'esecuzione e la relativa memoria deve essere rilasciata per essere disponibile per il riutilizzo. Con allocazioni e deallocazioni costanti, in genere il Garbage Collector deve essere eseguito più frequentemente, con ripercussioni negative sulle prestazioni e sull'esperienza utente.

In un interessante documento di Unity viene illustrato in dettaglio il funzionamento del Garbage Collector e vengono forniti suggerimenti per scrivere codice più efficiente dal punto di vista della gestione della memoria.
- [Optimizing garbage collection in Unity games](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069) (Ottimizzazione della Garbage Collection nei giochi Unity)

Una delle procedure più comuni che porta a un numero eccessivo di Garbage Collection è la pratica di non memorizzare nella cache i riferimenti a componenti e classi nello sviluppo in Unity. Tutti i riferimenti devono essere acquisiti durante Start() o Awake() e riutilizzati in funzioni successive come Update() o LateUpdate().

Altri suggerimenti rapidi:
- Usa la classe [StringBuilder](/dotnet/api/system.text.stringbuilder) di C# per compilare dinamicamente stringhe complesse in fase di runtime
- Rimuovi le chiamate a Debug.Log() quando non sono più necessarie, in quanto vengono comunque eseguite in tutte le versioni delle build di un'app
- Se la tua app olografica di solito richiede molta memoria, considera la possibilità di chiamare [_**System.GC.Collect()**_](/dotnet/api/system.gc.collect) durante le fasi di caricamento, ad esempio durante la presentazione di una schermata di caricamento o di transizione

#### <a name="object-pooling"></a>Pooling di oggetti

Il pooling di oggetti è una tecnica molto usata per ridurre i costi di continue allocazioni e deallocazioni di oggetti. Viene eseguito allocando un pool di grandi dimensioni di oggetti identici e riutilizzando le istanze inattive disponibili di questo pool invece di generare ed eliminare costantemente gli oggetti nel tempo. I pool di oggetti sono la soluzione ideale per i componenti riutilizzabili con durata variabile durante l'esecuzione di un'app.

- [Esercitazione sul pooling di oggetti in Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Prestazioni in fase di avvio

Provare ad avviare l'app con una scena più piccola e quindi usare *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* per caricare il resto della scena. Ciò consente all'app di giungere a uno stato interattivo il più velocemente possibile. Si potrebbe registrare un considerevole picco nella CPU mentre è in corso l'attivazione della nuova scena e per qualsiasi contenuto sottoposto a rendering potrebbero verificarsi problemi di stuttering o di blocco. Un modo per ovviare a questo problema consiste nell'impostare la proprietà AsyncOperation.allowSceneActivation su "false" per la scena che viene caricata, attendere il caricamento della scena, far diventare nera la schermata e quindi reimpostare la proprietà su "true" per completare l'attivazione della scena.

Ricorda che, durante il caricamento della scena di avvio, all'utente verrà visualizzata la schermata iniziale olografica.

## <a name="see-also"></a>Vedere anche
- [Optimizing graphics rendering in Unity games](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069) (Ottimizzazione del rendering della grafica nei giochi Unity)
- [Optimizing garbage collection in Unity games](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069) (Ottimizzazione della Garbage Collection nei giochi Unity)
- [Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) (Procedure consigliate per la fisica [Unity])
- [Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html) (Ottimizzazione degli script [Unity])