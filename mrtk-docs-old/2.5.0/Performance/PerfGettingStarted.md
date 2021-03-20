---
title: PefGettingStarted
description: Documentazione per comprendere e modificare la conformità in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: d982de8e546585e254d47679944e4ba169136d67
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687441"
---
# <a name="performance"></a>Prestazioni

## <a name="getting-started"></a>Introduzione

Il modo più semplice per razionalizzare le prestazioni è tramite framerate o il numero di volte in cui l'applicazione può eseguire il rendering di un'immagine al secondo. È importante soddisfare il framerate di destinazione, come indicato dalla piattaforma di destinazione (ad esempio [Realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)e così via. Ad esempio, in HoloLens, il framerate di destinazione è 60 FPS. Le applicazioni con framerate ridotto possono comportare esperienze utente deteriorate, come la [stabilizzazione olografica](hologram-Stabilization.md)peggiorata, il rilevamento del mondo, il rilevamento manuale e altro ancora. Per aiutare gli sviluppatori a tenere traccia e ottenere la framerate di qualità, il Toolkit di realtà mista offre un'ampia gamma di strumenti e script.

### <a name="visual-profiler"></a>Visual Profiler

Per tenere traccia continuamente delle prestazioni per il ciclo di vita dello sviluppo, è consigliabile visualizzare sempre un oggetto visivo framerate durante l'esecuzione & il debug di un'applicazione. Il Toolkit di realtà mista fornisce lo strumento di diagnostica di [Visual Profiler](../features/Diagnostics/UsingVisualProfiler.md) che fornisce informazioni in tempo reale sugli fps correnti e sull'utilizzo della memoria nella visualizzazione dell'applicazione. È possibile configurare Visual Profiler tramite le [impostazioni del sistema di diagnostica](../features/Diagnostics/DiagnosticsSystemGettingStarted.md) nel [controllo profili MRTK](../out-of-scope/MixedRealityConfigurationGuide.md).

Inoltre, è particolarmente importante usare Visual Profiler per tenere traccia del framerate durante l'esecuzione nel dispositivo anziché nell'editor di Unity o in un emulatore. I risultati più accurati delle prestazioni verranno rappresentati quando vengono eseguiti nel dispositivo con [Build di configurazione di rilascio](https://docs.microsoft.com/visualstudio/debugger/how-to-set-debug-and-release-configurations?view=vs-2019).

> [!NOTE]
> Se si compila per la realtà mista di Windows, eseguire la distribuzione con [Build di configurazione Master](https://docs.microsoft.com/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![Interfaccia di Visual Profiler](../features/Images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>Ottimizza finestra

La [finestra di ottimizzazione di MRTK](../features/Tools/OptimizeWindow.md) offre strumenti per informazioni e automazione per aiutare gli sviluppatori di realtà mista a configurare il proprio ambiente per ottenere risultati ottimali e identificare potenziali colli di bottiglia nella propria scena & asset. Alcune configurazioni chiave in Unity possono contribuire a offrire risultati notevolmente più ottimizzati per i progetti di realtà mista.

In genere, queste impostazioni coinvolgono configurazioni di rendering ideali per la realtà mista. Le applicazioni di realtà miste sono univoche rispetto allo sviluppo di grafica 3D tradizionale in quanto sono presenti due schermate, ad esempio due occhi) per eseguire il rendering dell'intera scena.

Le impostazioni consigliate indicate di seguito possono essere configurate automaticamente in un progetto Unity sfruttando la finestra ottimizza MRTK.

![Impostazioni finestra ottimizza MRTK](../features/Images/Performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Profiler Unity

[Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html) è uno strumento utile per analizzare i dettagli delle prestazioni dell'applicazione a un livello frame per fotogramma.

#### <a name="time-spent-on-the-cpu"></a>Tempo impiegato per la CPU

![Esempio di grafico di Unity Profiler](../features/Images/Performance/UnityProfilerGraph.png)

Per mantenere le frequenze dei fotogrammi confortevoli (in genere 60 fotogrammi al secondo), le applicazioni devono ottenere un tempo massimo di frame di 16,6 millisecondi di tempo di CPU. Per identificare il costo della funzionalità MRTK, Microsoft Mixed Reality Toolkit contiene un marcatore per i percorsi del codice del ciclo interno (per frame). Questi marcatori usano il formato seguente per semplificare la comprensione delle funzionalità specifiche utilizzate:

```
[MRTK] className.methodName
```

> [!Note]
> Potrebbero essere presenti dati aggiuntivi che seguono il nome del metodo. Viene usato per identificare funzionalità eseguite in modo condizionale e potenzialmente costose che possono essere evitate da piccole modifiche al codice dell'applicazione.

![Esempio di gerarchia di Unity Profiler](../features/Images/Performance/UnityProfilerHierarchy.png)

In questo esempio la gerarchia è stata espansa per mostrare che il metodo UpdateHandData della classe WindowsMixedRealityArticulatedHand sta consumando 0,44 ms di tempo di CPU durante l'analisi del frame. Questi dati possono essere usati per determinare se un problema di prestazioni è correlato al codice dell'applicazione o altrove nel sistema.

Si consiglia agli sviluppatori di instrumentare il codice dell'applicazione in modo analogo. Le aree di interesse primarie per la strumentazione del codice dell'applicazione si trovano all'interno dei gestori di eventi, perché questi metodi vengono addebitati al ciclo di aggiornamento MRTK durante la generazione degli eventi. I tempi elevati dei frame all'interno del ciclo di aggiornamento MRTK possono essere indicativi di codice costoso nei metodi del gestore eventi.

## <a name="recommended-settings-for-unity"></a>Impostazioni consigliate per Unity

### <a name="single-pass-instanced-rendering"></a>Rendering di Single-Pass istanza

La configurazione di rendering predefinita per XR in Unity è [MultiPASS](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html). Questa impostazione indica a Unity di eseguire due volte l'intera pipeline di rendering, una volta per ogni occhio. Questa operazione può essere ottimizzata selezionando invece il [rendering con istanza Single Pass](https://docs.unity3d.com/Manual/SinglePassInstancing.html) . Questa configurazione sfrutta le [matrici di destinazione di rendering](https://en.wikipedia.org/wiki/Multiple_Render_Targets) per poter eseguire una singola chiamata di disegnare che istanze nella destinazione di [rendering](https://en.wikipedia.org/wiki/Render_Target) appropriata per ogni occhio. Questa modalità consente inoltre di eseguire tutto il rendering in una singola esecuzione della pipeline di rendering. Quindi, la selezione del rendering con istanza a passaggio singolo come percorso di rendering per un'applicazione di realtà mista può [risparmiare tempo sostanziale sia sulla CPU & GPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) sia sulla configurazione di rendering consigliata.

Tuttavia, per eseguire una singola chiamata di progetto per ogni mesh a ogni occhio, le [istanze GPU](https://docs.unity3d.com/Manual/GPUInstancing.html) devono essere supportate da tutti gli shader. La creazione di istanze consente alla GPU di effettuare il multimultiplexing di chiamate a tutti gli occhi Per impostazione predefinita, gli shader incorporati Unity e lo [shader standard MRTK](../features/README_MRTKStandardShader.md) contengono le istruzioni necessarie per la creazione di istanze nel codice dello shader. Se invece si scrivono shader personalizzati per Unity, è possibile che questi shader debbano essere aggiornati per supportare il rendering a istanza singola di pass.

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

### <a name="quality-settings"></a>Impostazioni qualità

Unity fornisce [set di impostazioni per controllare la qualità](https://docs.unity3d.com/Manual/class-QualitySettings.html) del rendering per ogni endpoint della piattaforma. Questi set di impostazioni controllano le funzionalità grafiche che possono essere abilitate, ad esempio le ombre, l'anti-aliasing, l'illuminazione globale e altro ancora. È consigliabile ridurre queste impostazioni e ottimizzare il numero di calcoli eseguiti durante il rendering.

*Passaggio 1:* Aggiornare i progetti Unity della realtà mista per usare l'impostazione del livello di *qualità bassa*  
**Modifica**  >  **Impostazioni progetto**, quindi selezionare la categoria **qualità** > selezionare *bassa qualità* per la piattaforma UWP

*Passaggio 2:* Per ogni file di scena Unity, disabilitare l' [illuminazione globale in tempo reale](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**Finestra**  >  di **Rendering**  >  di **Impostazioni**  >  di illuminazione [Deselezionare l' *illuminazione globale in tempo reale*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>Condivisione buffer di profondità (HoloLens)

Se lo sviluppo per la piattaforma di realtà mista di Windows e in particolare HoloLens, l'abilitazione della *condivisione del buffer di profondità* nelle impostazioni di *XR* può contribuire alla [stabilizzazione ologramma](../Performance/Hologram-Stabilization.md) Tuttavia, l'elaborazione del buffer di profondità può comportare un costo in termini di prestazioni, in particolare se si utilizza il [formato di profondità a 24 bit](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html). È quindi *consigliabile* configurare il buffer di profondità sulla precisione a 16 bit.

Se si verifica un [conflitto z](https://en.wikipedia.org/wiki/Z-fighting) a causa del formato bit più basso, verificare che il [piano di ritaglio](https://docs.unity3d.com/Manual/class-Camera.html) di tutte le fotocamere sia impostato sul valore più basso possibile per l'applicazione. Per impostazione predefinita, Unity imposta un piano di ritaglio lungo di 1000 m. In HoloLens, un piano di ritaglio a 50m è in genere più che sufficiente per la maggior parte degli scenari di applicazione.

> [!NOTE]
> Se si utilizza il *formato di profondità a 16 bit*, gli effetti necessari sul buffer dello stencil non funzioneranno perché [Unity non crea un buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il *formato di profondità a 24 bit* , in genere viene creato un buffer di stencil a 8 bit, se applicabile sulla piattaforma grafica dell'endpoint.
>
> Se si utilizza un [componente mask](https://docs.unity3d.com/Manual/script-Mask.html) che richiede il buffer dello stencil, provare a utilizzare [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) , che non richiede il buffer dello stencil e pertanto può essere utilizzato in combinazione con un formato di *profondità a 16 bit*.

> [!NOTE]
> Per determinare rapidamente quali oggetti di una scena non scrivono visivamente il buffer di profondità, è possibile usare l'utilità di [ *rendering del buffer di profondità*](../out-of-scope/MixedRealityConfigurationGuide.md#editor-utilities) sotto le impostazioni dell' *Editor* nel profilo di configurazione MRTK.

### <a name="optimize-mesh-data"></a>Ottimizzare i dati mesh

Le impostazioni [Ottimizza dati mesh](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) tentano di rimuovere gli attributi Vertex non usati all'interno dell'applicazione. L'impostazione esegue questa operazione eseguendo ogni passaggio dello shader in ogni materiale presente in ogni mesh della compilazione. Si tratta di una soluzione ideale per le prestazioni dei dati di gioco e di runtime, ma può ostacolare drasticamente i tempi di compilazione

È consigliabile disabilitare questa impostazione durante lo sviluppo e riabilitarla durante la creazione della compilazione "Master". L'impostazione è disponibile in **modifica**  >  **Impostazioni progetto**  >  **lettore**  >  **altre impostazioni**  >  **Ottimizza dati mesh**.

## <a name="general-recommendations"></a>Indicazioni generali

Le prestazioni possono essere una sfida ambigua e in costante evoluzione per gli sviluppatori di realtà mista e la gamma di informazioni per razionalizzare le prestazioni è vasta. Sono disponibili alcuni suggerimenti generali per comprendere come approcciare le prestazioni di un'applicazione.

È utile per semplificare l'esecuzione di un'applicazione in componenti eseguiti sulla *CPU* o sulla *GPU* e, di conseguenza, determinare se un'app è vincolata da uno dei due componenti.  È possibile che si verifichino colli di bottiglia che si estendono a entrambe le unità di elaborazione e ad alcuni scenari univoci che devono essere analizzati attentamente. Tuttavia, per iniziare, è opportuno comprendere la posizione in cui viene eseguita un'applicazione per il maggior numero di tempo.

### <a name="gpu-bounded"></a>GPU limitata

Poiché la maggior parte delle piattaforme per le applicazioni con realtà mista Usa il [rendering stereoscopico](https://en.wikipedia.org/wiki/Stereoscopy), è molto comune eseguire il delimitatore della GPU a causa della natura del rendering di uno schermo a "doppia larghezza". Inoltre, le piattaforme per la realtà mista per dispositivi mobili, ad esempio HoloLens o Oculus, saranno limitate dalla potenza di elaborazione GPU & CPU di livello mobile.

Quando ci si concentra sulla GPU, in genere sono presenti due fasi importanti che devono essere completate da un'applicazione ogni frame.

1. Esegui [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. Eseguire il [pixel shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (noto anche come frammento shader)

Senza approfondire il campo complesso della grafica dei computer & le [pipeline di rendering](https://en.wikipedia.org/wiki/Graphics_pipeline), ogni fase dello shader è un programma che viene eseguito sulla GPU per produrre quanto segue.

1. I vertex shader trasformano i vertici mesh in coordinate nello spazio dello schermo, ad esempio codice eseguito per vertice)
2. I pixel shader calcolano il colore da creare per un pixel e un frammento di mesh specificati (ad esempio esecuzione del codice per pixel)

Per quanto riguarda l'ottimizzazione delle prestazioni, è in genere più proficuo concentrarsi sull'ottimizzazione delle operazioni nel pixel shader. È possibile che un'applicazione debba solo creare un cubo che sarà costituito solo da 8 vertici. Tuttavia, lo spazio dello schermo occupato dal cubo è probabilmente l'ordine di milioni di pixel. Quindi, riducendo il codice dello shader, le 10 operazioni consentono di risparmiare molto più lavoro se ridotto sulla pixel shader rispetto al vertex shader.

Questo è uno dei motivi principali per sfruttare lo shader [standard MRTK](../features/README_MRTKStandardShader.md) poiché questo shader esegue in genere molte meno istruzioni per pixel & vertice rispetto allo shader standard Unity, ottenendo risultati estetici paragonabili.

|    Ottimizzazioni CPU      |             Ottimizzazioni GPU              |
|---------------------------|--------------------------------------------|
| Logica di simulazione delle app      | Operazioni di rendering |
| Semplificare la fisica          | Ridurre i calcoli di illuminazione |
| Semplifica animazioni       | Ridurre il numero di poligoni & numero di oggetti che è stato disegnato |
| Gestisci Garbage Collection | Ridurre il numero di oggetti trasparenti |
| Riferimenti alla cache          | Evitare effetti di post-elaborazione/schermo intero  |

### <a name="draw-call-instancing"></a>Creazione di istanze di chiamata

Uno degli errori più comuni in Unity che consente di ridurre le prestazioni consiste nel clonare i materiali in fase di esecuzione. Se GameObject condividono lo stesso materiale e/o sono la stessa mesh, possono essere ottimizzate in chiamate a singolo progetto tramite tecniche come l'invio in *[batch statico](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, l'invio in *[batch dinamico](https://docs.unity3d.com/Manual/DrawCallBatching.html)* e la creazione di *[istanze GPU](https://docs.unity3d.com/Manual/GPUInstancing.html)*. Tuttavia, se gli sviluppatori modificano le proprietà del materiale di un [renderer](https://docs.unity3d.com/ScriptReference/Renderer-material.html) in fase di esecuzione, Unity creerà una copia clone del materiale assegnato.

Se, ad esempio, in una scena sono presenti cubi 100, uno sviluppatore potrebbe voler assegnare un colore univoco a ogni fase di esecuzione. L'accesso di [*renderer. Material. Color*](https://docs.unity3d.com/ScriptReference/Material-color.html) in C# renderà Unity la creazione di un nuovo materiale in memoria per questo particolare renderer/GameObject. Ognuno dei cubi 100 avrà il proprio materiale e pertanto non sarà possibile unirli in una sola chiamata di progetto, ma di100 VENTERÀ una richiesta di chiamata di chiamata di richiamo dalla CPU alla GPU.

Per ovviare a questo ostacolo e comunque assegnare un colore univoco per cubo, gli sviluppatori devono utilizzare [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).

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

## <a name="unity-performance-tools"></a>Strumenti per le prestazioni Unity

Unity offre strumenti eccezionali per le prestazioni incorporati nell'editor.

- [Profiler Unity](https://docs.unity3d.com/Manual//Profiler.html)
- [Debugger frame Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

Se si stima il compromesso di prestazioni elevate tra uno shader e un altro, è utile compilare ogni shader e visualizzare il numero di operazioni per ogni fase dello shader. Questa operazione può essere eseguita selezionando un [Asset shader](https://docs.unity3d.com/Manual/class-Shader.html) e facendo clic sul pulsante *Compila e Mostra codice* . In questo modo si compileranno tutte le varianti dello shader e si aprirà Visual Studio con i risultati. Nota: i risultati statistici prodotti possono variare a seconda delle funzionalità abilitate per i materiali che usano lo shader specificato. Unity compilerà solo le varianti dello shader utilizzate direttamente nel progetto corrente.

Esempio di statistiche shader standard Unity

![Statistiche dello shader standard Unity](../features/Images/Performance/UnityStandardShader-Stats.PNG)

Esempio di statistiche shader standard MRTK

![Statistiche dello shader standard MRTK](../features/Images/Performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>Vedi anche

### <a name="unity"></a>Unity

- [Ottimizzazione delle prestazioni Unity per principianti](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Esercitazioni sull'ottimizzazione delle prestazioni Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Procedure consigliate per l'ottimizzazione Unity](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [Ottimizzazione delle prestazioni grafiche](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [Guida pratica di ottimizzazione per dispositivi mobili](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [Impostazioni consigliate per Unity](https://docs.microsoft.com/windows/mixed-reality/recommended-settings-for-unity)
- [Informazioni sulle prestazioni per la realtà mista](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Consigli sulle prestazioni per Unity](https://docs.microsoft.com/windows/mixed-reality/performance-recommendations-for-unity)
- [Guida a Unity Event Tracing for Windows](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [Linee guida relative alle prestazioni](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [Strumenti per le prestazioni](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>Ottimizzazione mesh

- [Ottimizzare i modelli 3D](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Procedure consigliate per la conversione e l'ottimizzazione di modelli 3D in tempo reale](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)
