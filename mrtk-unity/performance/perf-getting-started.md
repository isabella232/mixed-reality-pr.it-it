---
title: Prestazioni
description: Documentazione per comprendere e modificare la preformance in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 6c8e060af585d7994774ea0bb575b6e5172b9558
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281766"
---
# <a name="performance"></a>Prestazioni

## <a name="getting-started"></a>Guida introduttiva

Il modo più semplice per razionalizzare le prestazioni è tramite framerate o quante volte l'applicazione può eseguire il rendering di un'immagine al secondo. È importante soddisfare il framerate di destinazione, come indicato dalla piattaforma di destinazione (ad esempio [Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)e così via). Ad esempio, nel HoloLens, il framerate di destinazione è 60 FPS. Le applicazioni a bassa frequenza di fotogrammi possono causare esperienze utente peggiorate, ad esempio stabilizzazione [ologramma](../performance/hologram-stabilization.md)peggiorata, tracciamento del mondo, tracciamento manuale e altro ancora. Per consentire agli sviluppatori di tenere traccia e ottenere framerate di qualità, l'Toolkit di realtà mista offre un'ampia gamma di strumenti e script.

### <a name="visual-profiler"></a>Profiler visivo

Per tenere traccia continuamente delle prestazioni nel corso della durata dello sviluppo, è consigliabile visualizzare sempre un oggetto visivo con framerate durante l'& debug di un'applicazione. L'Toolkit realtà mista fornisce lo strumento di diagnostica [Visual Profiler](../features/diagnostics/using-visual-profiler.md) che fornisce informazioni in tempo reale sull'fps corrente e sull'utilizzo della memoria nella visualizzazione dell'applicazione. Visual Profiler può essere configurato tramite il sistema di [diagnostica Impostazioni](../features/diagnostics/diagnostics-system-getting-started.md) controllo profili [MRTK](../configuration/mixed-reality-configuration-guide.md).

Inoltre, è particolarmente importante usare Visual Profiler per tenere traccia della frequenza dei fotogrammi durante l'esecuzione nel dispositivo anziché nell'editor di Unity o in un emulatore. I risultati delle prestazioni più accurati verranno visualizzati durante l'esecuzione nel dispositivo con [build di configurazione release](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019).

> [!NOTE]
> Se si compila per Windows Mixed Reality, eseguire la distribuzione con build [di configurazione MASTER](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![Interfaccia di Visual Profiler](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>Finestra Ottimizza

La [finestra di ottimizzazione MRTK](../features/tools/optimize-window.md) offre informazioni e strumenti di automazione per aiutare gli sviluppatori di realtà mista a configurare il proprio ambiente per ottenere risultati ottimali e identificare potenziali colli di bottiglia nella scena & asset. Alcune configurazioni chiave in Unity consentono di ottenere risultati sostanzialmente più ottimizzati per i progetti di realtà mista.

In genere, queste impostazioni comportano configurazioni di rendering ideali per la realtà mista. Le applicazioni di realtà mista sono univoche rispetto allo sviluppo tradizionale di grafica 3D in cui sono presenti due schermate, due occhi) per il rendering per l'intera scena.

Le impostazioni consigliate a cui si fa riferimento di seguito possono essere configurate automaticamente in un progetto Unity sfruttando la finestra di ottimizzazione MRTK.

![Finestra di ottimizzazione MRTK Impostazioni](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Unity Profiler

[Unity Profiler è](https://docs.unity3d.com/Manual/ProfilerWindow.html) uno strumento utile per analizzare i dettagli delle prestazioni dell'applicazione a livello fotogramma per frame.

#### <a name="time-spent-on-the-cpu"></a>Tempo impiegato per la CPU

![Esempio di Graph di Unity Profiler](../features/images/performance/UnityProfilerGraph.png)

Per mantenere una frequenza di fotogrammi comoda (in genere 60 fotogrammi al secondo), le applicazioni devono ottenere un tempo di fotogramma massimo di 16,6 millisecondi di tempo cpu. Per identificare il costo della funzionalità MRTK, microsoft Mixed Reality Toolkit contiene marcatori per i percorsi di codice del ciclo interno (per frame). Questi marcatori usano il formato seguente, per facilitare la comprensione della funzionalità specifica in uso:

```
[MRTK] className.methodName
```

> [!Note]
> Potrebbero essere presenti dati aggiuntivi dopo il nome del metodo. Viene usato per identificare funzionalità potenzialmente costose eseguite in modo condizionale che possono essere evitate da piccole modifiche al codice dell'applicazione.

![Esempio di gerarchia del profiler Unity](../features/images/performance/UnityProfilerHierarchy.png)

In questo esempio la gerarchia è stata espansa per mostrare che il metodo UpdateHandData della classe WindowsMixedRealityArticulatedHand sta consumando 0,44 ms di tempo cpu durante il frame analizzato. Questi dati possono essere usati per determinare se un problema di prestazioni è correlato al codice dell'applicazione o da un'altra parte del sistema.

È consigliabile che gli sviluppatori instrumentino il codice dell'applicazione in modo simile. Le aree principali di interesse per la strumentazione del codice dell'applicazione sono all'interno dei gestori eventi, in quanto questi metodi vengono addebitati al ciclo di aggiornamento MRTK quando vengono generati gli eventi. I tempi di frame elevati all'interno del ciclo di aggiornamento MRTK possono essere indicativi del codice costoso nei metodi del gestore eventi.

## <a name="recommended-settings-for-unity"></a>Impostazioni consigliate per Unity

### <a name="single-pass-instanced-rendering"></a>Single-Pass rendering con istanze

La configurazione di rendering predefinita per XR in Unity è [Multi-pass](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html). Questa impostazione indica a Unity di eseguire l'intera pipeline di rendering due volte, una volta per ogni occhio. Questa opzione può essere ottimizzata selezionando [rendering con istanza a passaggio](https://docs.unity3d.com/Manual/SinglePassInstancing.html) singolo. Questa configurazione sfrutta le [matrici di destinazione](https://en.wikipedia.org/wiki/Multiple_Render_Targets) di rendering per poter eseguire una singola chiamata di disegno che istanze nella destinazione [di rendering appropriata](https://en.wikipedia.org/wiki/Render_Target) per ogni occhio. Inoltre, questa modalità consente di eseguire tutto il rendering in una singola esecuzione della pipeline di rendering. Pertanto, la selezione del rendering & istanza a passaggio singolo come percorso di rendering per un'applicazione di realtà mista consente di risparmiare molto tempo [& GPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) ed è la configurazione di rendering consigliata.

Tuttavia, per eseguire una singola chiamata di disegno per ogni mesh a ogni occhio, le istanze [GPU](https://docs.unity3d.com/Manual/GPUInstancing.html) devono essere supportate da tutti gli shader. L'instancing consente alla GPU di eseguire chiamate multiplex di disegno su entrambi gli occhi. Gli shader predefiniti di Unity e lo [shader STANDARD MRTK](../features/rendering/mrtk-standard-shader.md) contengono per impostazione predefinita le istruzioni di creazione delle istanze necessarie nel codice dello shader. Se tuttavia si scrivono shader personalizzati per Unity, potrebbe essere necessario aggiornarlo per supportare il rendering con istanza a passaggio singolo.

#### <a name="example-code-for-custom-shader"></a>[Codice di esempio per lo shader personalizzato](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a>Impostazioni di qualità

Unity fornisce [set di impostazioni per controllare la qualità](https://docs.unity3d.com/Manual/class-QualitySettings.html) del rendering per ogni endpoint della piattaforma. Questi set di impostazioni controllano quali funzionalità grafiche possono essere abilitate, ad esempio ombreggiature, anti-aliasing, illuminazione globale e altro ancora. È consigliabile ridurre queste impostazioni e ottimizzare il numero di calcoli eseguiti durante il rendering.

*Passaggio 1:* Aggiornare i progetti Unity di realtà mista per usare *l'impostazione Livello di bassa* qualità  
**Modifica**  >  **Project Impostazioni**, quindi selezionare la categoria **Qualità** > selezionare *Bassa qualità* per la piattaforma UWP

*Passaggio 2:* Per ogni file di scena unity, disabilitare [l'illuminazione globale in tempo reale](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**Finestra**  >  **Rendering**  >  **Illuminazione Impostazioni**  >  [Deselezionare *Illuminazione globale in tempo reale*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>Condivisione buffer di profondità (HoloLens)

Se si sviluppa per la piattaforma Windows Mixed Reality e in  particolare HoloLens, l'abilitazione della condivisione buffer di profondità in *XR Impostazioni* può essere utile per la [stabilizzazione degli ologrammi.](../performance/hologram-stabilization.md) Tuttavia, l'elaborazione del buffer di profondità può sostenere un costo delle prestazioni, in particolare se si usa il formato di [profondità a 24 bit](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html). È quindi consigliabile *configurare* il buffer di profondità sulla precisione a 16 bit.

Se [lo z-fighting](https://en.wikipedia.org/wiki/Z-fighting) si verifica a causa del formato in bit inferiore, verificare che il piano di [ritaglio](https://docs.unity3d.com/Manual/class-Camera.html) lontano di tutte le fotocamere sia impostato sul valore più basso possibile per l'applicazione. Unity per impostazione predefinita imposta un piano di ritaglio lontano di 1000 metri. In HoloLens, un piano di ritaglio lontano di 50 metri è in genere più che sufficiente per la maggior parte degli scenari di applicazione.

> [!NOTE]
> Se si usa il formato di profondità a *16 bit,* gli effetti necessari del buffer di stencil non funzioneranno perché Unity non crea un [buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il formato di profondità a *24 bit,* in genere verrà creato un buffer di stencil a 8 bit, se applicabile nella piattaforma grafica dell'endpoint.
>
> Se si usa un componente [Mask](https://docs.unity3d.com/Manual/script-Mask.html) che richiede il buffer di stencil, prendere in considerazione l'uso di [RectMask2D,](https://docs.unity3d.com/Manual/script-RectMask2D.html) che non richiede il buffer di stencil e può quindi essere usato in combinazione con un formato di profondità a *16 bit.*

> [!NOTE]
> Per determinare rapidamente gli oggetti in una scena che non scrivono visivamente nel  buffer di profondità, è possibile usare l'utilità [ *Buffer*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) di profondità di rendering nel Impostazioni Editor nel profilo di configurazione MRTK.

### <a name="optimize-mesh-data"></a>Ottimizzare i dati mesh

Le [impostazioni ottimizza dati mesh](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) provano a rimuovere gli attributi dei vertici inutilizzati all'interno dell'applicazione. L'impostazione esegue questa operazione eseguendo ogni passaggio dello shader in ogni materiale presente in ogni mesh nella compilazione. Questo è un'operazione buona per le dimensioni dei dati di gioco e le prestazioni di runtime, ma può ostacolare drasticamente i tempi di compilazione.

È consigliabile disabilitare questa impostazione durante lo sviluppo e riattivarla durante la creazione della compilazione "Master". L'impostazione è disponibile in **Edit**  >  **Project Impostazioni** Player Other Impostazioni Optimize Mesh Data  >    >    >  (Modifica Project Impostazioni Player Other Impostazioni Optimize Mesh Data ).

## <a name="general-recommendations"></a>Indicazioni generali

Le prestazioni possono essere una sfida ambigua e in continua evoluzione per gli sviluppatori di realtà mista e lo spettro di conoscenze per razionalizzare le prestazioni è vasto. Esistono tuttavia alcune raccomandazioni generali per comprendere come affrontare le prestazioni di un'applicazione.

È utile semplificare l'esecuzione di un'applicazione nei componenti eseguiti nella *CPU* o nella *GPU* e quindi identificare se un'app è vincolata da uno dei due componenti.  Possono esserci colli di bottiglia che si estendono su unità di elaborazione e alcuni scenari univoci che devono essere esaminati con attenzione. Tuttavia, per iniziare, è bene capire dove un'applicazione è in esecuzione per la maggior parte del tempo.

### <a name="gpu-bounded"></a>GPU delimitata

Poiché la maggior parte delle piattaforme per le applicazioni di realtà mista usa il [rendering stereoscopico,](https://en.wikipedia.org/wiki/Stereoscopy)è molto comune essere delimitati da GPU a causa della natura del rendering di uno schermo "a doppia larghezza". Futhermore, le piattaforme di realtà mista per dispositivi mobili, ad esempio HoloLens o Oculus Quest, saranno limitate dalla potenza di elaborazione della GPU & CPU di classe mobile.

Quando ci si concentra sulla GPU, in genere un'applicazione deve completare ogni frame in due fasi importanti.

1. Eseguire il [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. Eseguire il [pixel shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (noto anche come fragment shader)

Senza un'approfondita conoscenza del campo complesso della grafica computer & pipeline di [rendering,](https://en.wikipedia.org/wiki/Graphics_pipeline)ogni fase dello shader è un programma che viene eseguito nella GPU per produrre quanto segue.

1. I vertex shader trasformano i vertici della mesh in coordinate nello spazio dello schermo (ad esempio codice eseguito per vertice)
2. I pixel shader calcolano il colore da disegnare per un determinato pixel e frammento di mesh (ad esempio codice eseguito per pixel)

Per quanto riguarda l'ottimizzazione delle prestazioni, è in genere più fruttuoso concentrarsi sull'ottimizzazione delle operazioni nel pixel shader. Un'applicazione potrebbe dover disegnare solo un cubo che sarà di soli 8 vertici. Tuttavia, lo spazio dello schermo che occupa il cubo è probabilmente nell'ordine di milioni di pixel. Di conseguenza, riducendo il codice dello shader, ad esempio 10 operazioni, è possibile risparmiare molto più lavoro se ridotto nel pixel shader rispetto al vertex shader.

Questo è uno dei motivi principali per sfruttare lo [shader MRTK Standard](../features/rendering/mrtk-standard-shader.md) perché in genere esegue molte meno istruzioni per pixel & vertice rispetto allo shader Unity Standard, ottenendo risultati paragonabili.

|    Ottimizzazioni della CPU      |             Ottimizzazioni GPU              |
|---------------------------|--------------------------------------------|
| Logica di simulazione delle app      | Operazioni di rendering |
| Semplificare la fisica          | Ridurre i calcoli di illuminazione |
| Semplificare le animazioni       | Ridurre il numero di poligoni & numero di oggetti drawable |
| Gestire Garbage Collection | Ridurre il numero di oggetti trasparenti |
| Riferimenti alla cache          | Evitare effetti post-elaborazione/schermo intero  |

### <a name="draw-call-instancing"></a>Creare istanze di chiamata

Uno degli errori più comuni in Unity che riduce le prestazioni è la clonazione dei materiali in fase di esecuzione. Se i GameObject condividono lo stesso materiale e/o sono la stessa mesh, possono essere ottimizzati in singole chiamate di disegno tramite tecniche come l'invio in *[batch](https://docs.unity3d.com/Manual/DrawCallBatching.html)* statico, l'invio in *[batch](https://docs.unity3d.com/Manual/DrawCallBatching.html)* dinamico e la creazione di istanze *[GPU.](https://docs.unity3d.com/Manual/GPUInstancing.html)* Tuttavia, se le proprietà di modifica dello sviluppatore del materiale di un [renderer](https://docs.unity3d.com/ScriptReference/Renderer-material.html) in fase di esecuzione, Unity creerà una copia clone del materiale assegnato.

Ad esempio, se in una scena sono presenti 100 cubi, uno sviluppatore potrebbe voler assegnare un colore univoco a ognuno di essi in fase di esecuzione. L'accesso [*di renderer.material.color*](https://docs.unity3d.com/ScriptReference/Material-color.html) in C# farà in modo che Unity crei un nuovo materiale in memoria per questo particolare renderer/GameObject. Ognuno dei 100 cubi avrà un proprio materiale e quindi non può essere unito in un'unica chiamata di disegno, ma diventerà invece 100 richieste di chiamata di disegno dalla CPU alla GPU.

Per superare questo ostacolo e assegnare comunque un colore univoco per ogni cubo, gli sviluppatori devono sfruttare [MaterialPropertyBlock.](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a>Strumenti per le prestazioni di Unity

Unity offre strumenti avanzati per le prestazioni incorporati nell'editor.

- [Unity Profiler](https://docs.unity3d.com/Manual//Profiler.html)
- [Unity Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)

Se si stima il compromesso approssimativo tra le prestazioni tra uno shader e un altro, è utile compilare ogni shader e visualizzare il numero di operazioni per ogni fase dello shader. A tale scopo, selezionare un [asset shader e](https://docs.unity3d.com/Manual/class-Shader.html) fare clic sul pulsante Compile and show code *(Compila e* mostra codice). Verranno compilate tutte le varianti di shader e verrà aperto Visual Studio con i risultati. Nota: i risultati delle statistiche prodotti possono variare a seconda delle funzionalità abilitate nei materiali che utilizzano lo shader specificato. Unity compilerà solo le varianti di shader usate direttamente nel progetto corrente.

Esempio di statistiche shader standard di Unity

![Statistiche shader standard unity 1](../features/images/performance/UnityStandardShader-Stats.PNG)

Esempio di statistiche dello shader MRTK Standard

![Statistiche shader standard MRTK 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>Vedi anche

### <a name="unity"></a>Unity

- [Ottimizzazione delle prestazioni di Unity per principianti](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Esercitazioni sull'ottimizzazione delle prestazioni di Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Procedure consigliate per l'ottimizzazione di Unity](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [Ottimizzazione delle prestazioni grafiche](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [Guida pratica all'ottimizzazione dei dispositivi mobili](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [Scelta Impostazioni per Unity](/windows/mixed-reality/recommended-settings-for-unity)
- [Informazioni sulle prestazioni per la realtà mista](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Consigli sulle prestazioni per Unity](/windows/mixed-reality/performance-recommendations-for-unity)
- [Guida a Event Tracing for Windows Unity](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [Linee guida relative alle prestazioni](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [Strumenti per le prestazioni](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>Ottimizzazione della mesh

- [Ottimizzare i modelli 3D](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Procedure consigliate per la conversione e l'ottimizzazione di modelli 3D in tempo reale](/dynamics365/mixed-reality/import-tool/best-practices)
