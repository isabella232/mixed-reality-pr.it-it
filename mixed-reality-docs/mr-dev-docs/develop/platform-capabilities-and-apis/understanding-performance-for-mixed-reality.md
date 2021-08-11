---
title: Informazioni sulle prestazioni per la realtà mista
description: Informazioni e dettagli avanzati per l'analisi e l'ottimizzazione Windows Mixed Reality delle app.
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Prestazioni, Ottimizzazione, CPU, GPU
ms.openlocfilehash: 394198011c40f0b90e2c5579f7e0ad8c4019b2a8cefcb1859c544afcbce47df6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193560"
---
# <a name="understanding-performance-for-mixed-reality"></a>Informazioni sulle prestazioni per la realtà mista

Questo articolo è un'introduzione alla comprensione del significato delle prestazioni per l'app di realtà mista.  L'esperienza utente può essere notevolmente degradata se l'applicazione non viene eseguita alla frequenza dei fotogrammi ottimale. Ologrammi apparirà instabile e il rilevamento della testa dell'ambiente non sarà accurato, con un'esperienza scadente per l'utente. Le prestazioni devono essere considerate una funzionalità di prima classe per lo sviluppo di realtà mista e non un'attività polacca.

Di recente è stata rilasciata un'applicazione denominata Quality Fundamentals che illustra problemi comuni di prestazioni, progettazione e ambiente e soluzioni per HoloLens 2 app. Questa app è un'ottima demo visiva per il contenuto seguente.

> [!div class="nextstepaction"]
> [Scaricare l'app Quality Fundamentals](https://www.microsoft.com/en-us/p/quality-fundamentals/9mwz852q88fw)

Di seguito sono elencati i valori della frequenza dei fotogrammi per ogni piattaforma di destinazione.

| Piattaforma | Frequenza fotogrammi di destinazione |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 FPS |
| [Windows Mixed Reality Ultra Pc](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pc](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

Il framework seguente illustra le procedure consigliate per raggiungere le frequenze dei fotogrammi di destinazione. È consigliabile leggere le [raccomandazioni sulle prestazioni per Unity per](../unity/performance-recommendations-for-unity.md) suggerimenti su come misurare e migliorare la frequenza dei fotogrammi nell'ambiente Unity.

## <a name="understanding-performance-bottlenecks"></a>Informazioni sui colli di bottiglia delle prestazioni

Se l'app ha un framerate sottoperformante, il primo passaggio consiste nell'analizzare e comprendere dove l'applicazione è a elevato utilizzo di calcolo. Esistono due processori principali responsabili del lavoro per il rendering della scena: la CPU e la GPU, ognuno dei quali gestisce aspetti diversi dell'app di realtà mista. I tre punti chiave in cui possono verificarsi colli di bottiglia sono: 

1. **Thread dell'app - CPU** -
    Responsabile della logica dell'app, inclusa l'elaborazione di input, animazioni, fisica e altra logica dell'app.
2. **Thread di rendering - CPU in GPU:** responsabile dell'invio delle chiamate di disegno alla GPU. Quando l'app vuole eseguire il rendering di un oggetto, ad esempio un cubo o un modello, questo thread invia una richiesta alla GPU per eseguire le operazioni.
3. **GPU:** in genere gestisce la pipeline grafica dell'applicazione per trasformare i dati 3D (modelli, trame e così via) in pixel. Produce infine un'immagine 2D da inviare sullo schermo del dispositivo.

![Durata di un frame](images/lifetime-of-a-frame.png)

In genere, HoloLens applicazioni saranno associate a GPU, ma non sempre. Usare gli strumenti e le tecniche seguenti per comprendere dove si verifica il collo di bottiglia dell'app specifica.

## <a name="how-to-analyze-your-application"></a>Come analizzare l'applicazione

Sono disponibili molti strumenti che consentono di comprendere il profilo delle prestazioni e i potenziali colli di bottiglia nell'applicazione di realtà mista. 

Di seguito sono riportati alcuni strumenti comuni che consentono di raccogliere informazioni approfondite sulla profilatura per l'applicazione:
- [Analizzatori delle prestazioni della grafica Intel](https://software.intel.com/gpa)
- [Visual Studio Debugger di grafica](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal Insights](../unreal/unreal-insights.md)
- [Pix](https://devblogs.microsoft.com/pix/)
- [GPU Pofiling in Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>Come profilare in qualsiasi ambiente

Un modo per determinare se l'app è associata a GPU o CPU è ridurre la risoluzione dell'output della destinazione di rendering. Riducendo il numero di pixel da calcolare, si ridurrà il carico della GPU. Il dispositivo eseguirà il rendering in una trama più piccola, quindi eseguirà l'up-sample per visualizzare l'immagine finale.

Dopo aver abbassato la risoluzione del rendering, se:
1) Il framerate **dell'applicazione** aumenta, quindi è probabile che sia **associato a GPU**
1) Framerate **dell'applicazione invariato,** è probabile che sia associato **alla CPU**

>[!NOTE]
>Unity consente di modificare facilmente la risoluzione della destinazione di rendering dell'applicazione in fase di esecuzione tramite la *[proprietà XRSettings.renderViewportScale.](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* L'immagine finale presentata nel dispositivo ha una risoluzione fissa. La piattaforma campiona l'output con risoluzione inferiore per creare un'immagine con risoluzione più elevata per il rendering sugli schermi. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Come migliorare l'applicazione

### <a name="cpu-performance-recommendations"></a>Consigli sulle prestazioni della CPU

In genere, la maggior parte del lavoro in un'applicazione di realtà mista sulla CPU comporta l'esecuzione della "simulazione" della scena e l'elaborazione della logica dell'applicazione. Le aree seguenti sono destinate all'ottimizzazione:

- Animazioni
- Fisica
- Allocazioni di memoria
- Algoritmi complessi ,ad esempio inverse kinematics, path-finding)

### <a name="gpu-performance-recommendations"></a>Consigli sulle prestazioni della GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Confronto tra larghezza di banda e fill rate
Quando si esegue il rendering di un frame nella GPU, un'applicazione viene associata alla larghezza di banda della memoria o fill rate.

- **La larghezza di** banda della memoria è la frequenza di lettura e scrittura che la GPU può eseguire dalla memoria
    - Per identificare le limitazioni della larghezza di banda, ridurre la qualità della trama e verificare se la velocità dei frame è migliorata.
    - In Unity modificare Qualità **trama** in **Modifica Project Impostazioni**  >    >  **[qualità Impostazioni](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **La frequenza** di riempimento si riferisce ai pixel che possono essere disegnati al secondo dalla GPU.
    - Per identificare fill rate limitazioni, ridurre la risoluzione dello schermo e verificare se la frequenza dei fotogrammi è migliorata. 
    - In Unity usare la *[proprietà XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

La larghezza di banda della memoria comporta in genere ottimizzazioni per:
1) Risoluzioni delle trame inferiori
2) Usare meno trame (normali, speculari e così via)

La frequenza di riempimento è incentrata sulla riduzione del numero di operazioni che devono essere calcolate per un pixel finale sottoposto a rendering, tra cui:
1) Numero di oggetti di cui eseguire il rendering/elaborazione
2) Numero di operazioni per shader
3) Numero di fasi DELLA GPU al risultato finale (geometry shader, effetti di post-elaborazione e così via)
4) Numero di pixel di cui eseguire il rendering (risoluzione dello schermo)

#### <a name="reduce-polygon-count"></a>Ridurre il numero di poligoni

I conteggi più elevati dei poligoni comportano più operazioni per la GPU, quindi la riduzione del numero di poligoni nella scena riduce il tempo di rendering. [](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) Esistono altri fattori che rendono costosa l'ombreggiatura della geometria, ma il conteggio dei poligoni è la metrica più semplice per determinare il lavoro necessario per il rendering di una scena.

#### <a name="limit-overdraw"></a>Limitare le sovrapposizioni

L'overdraw elevato si verifica quando viene eseguito il rendering di più oggetti ma non vengono visualizzati sullo schermo perché sono nascosti da un oggetto occluding. Imagine una parete che contiene oggetti dietro di essa. Tutta la geometria viene elaborata per il rendering, ma è necessario eseguire il rendering solo della parete opaca, con il risultato di operazioni non necessarie.

#### <a name="shaders"></a>Shader

Gli shader sono piccoli programmi eseguiti nella GPU ed eseguono due passaggi importanti nel rendering:
1) Determinazione dei vertici da disegnare e della posizione in cui si trova nello spazio dello schermo (Vertex shader)
    - Il vertex shader viene eseguito per vertice per ogni mesh.
2) Determinazione del colore di ogni pixel (Pixel shader)
    - Il pixel shader viene eseguito per pixel ed eseguito il rendering dalla geometria alla trama di rendering di destinazione.

In genere, gli shader esere diverse trasformazioni e calcoli di illuminazione. Anche se modelli di illuminazione complessi, ombreggiature e altre operazioni possono generare risultati straordinari, hanno anche un prezzo. La riduzione del numero di operazioni calcolate negli shader può ridurre notevolmente il lavoro necessario per la GPU per frame.

##### <a name="shader-coding-recommendations"></a>Raccomandazioni per la scrittura di codice shader

- Usare il filtro bilineare, quando possibile
- Ridisporre le espressioni in modo che usino funzioni intrinseche MAD per eseguire contemporaneamente una moltiplicazione e un'aggiunta
- Precalcolare il più possibile sulla CPU e passare come costanti al materiale
- **Favorire lo spostamento delle operazioni dal pixel shader al vertex shader**
    - In genere, il numero di vertici è molto più piccolo del numero di pixel (720p è 921.600 pixel, 1080p è 2.073.600 pixel e così via)

#### <a name="remove-gpu-stages"></a>Rimuovere le fasi della GPU

Gli effetti di post-elaborazione possono essere costosi e aumentare fill rate dell'applicazione, incluse tecniche di anti-aliasing come MSAA. In HoloLens è consigliabile evitare queste tecniche e altre fasi dello shader, ad esempio geometry, hull e compute shader.

## <a name="memory-recommendations"></a>Consigli sulla memoria

Un'allocazione di memoria eccessiva e operazioni di deallocazione possono comportare prestazioni incoerenti, frame bloccati e altri comportamenti dannosi. È particolarmente importante comprendere le considerazioni relative alla memoria durante lo sviluppo in Unity, poiché la gestione della memoria è controllata dal Garbage Collector.

#### <a name="object-pooling"></a>Pooling di oggetti

Il pool di oggetti è una tecnica comune per ridurre il costo delle allocazioni continue e delle deallocazione degli oggetti. Viene eseguito allocando un pool di grandi dimensioni di oggetti identici e riutilizzando le istanze inattive disponibili di questo pool invece di generare ed eliminare costantemente gli oggetti nel tempo. I pool di oggetti sono la soluzione ideale per i componenti riutilizzabili con durata variabile durante l'esecuzione di un'app.

## <a name="see-also"></a>Vedi anche
- [Consigli sulle prestazioni per Unity](../unity/performance-recommendations-for-unity.md)
- [Impostazioni consigliate per Unity](../unity/recommended-settings-for-unity.md)
- [Consigli sulle prestazioni per Unreal](../unreal/performance-recommendations-for-unreal.md)
- [Raccomandazioni sui materiali in Unreal](../unreal/unreal-materials.md)
- [Ottimizzare i modelli 3D](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Procedure consigliate per la conversione e l'ottimizzazione di modelli 3D in tempo reale](/dynamics365/mixed-reality/import-tool/best-practices)
- [Linee guida sulle prestazioni per gli artisti e i progettisti per Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Procedure consigliate per la realtà virtuale per Unreal](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)