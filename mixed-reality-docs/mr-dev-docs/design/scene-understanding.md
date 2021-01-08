---
title: Informazioni sulle scene
description: Informazioni su come sviluppare con la comprensione della scena per HoloLens, inclusi SDK, funzionalità e scenari di utilizzo comuni.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, realtà mista di Windows, Unity, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, occlusione, SDK
ms.openlocfilehash: c4485c5501300d6ca629f4e587fde1f88eea7ea5
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008871"
---
# <a name="scene-understanding"></a>Informazioni sulle scene

La comprensione delle scene fornisce agli sviluppatori di realtà mista una rappresentazione dell'ambiente di alto livello strutturata progettata per rendere intuitivo lo sviluppo di applicazioni compatibili con l'ambiente. Questa operazione viene eseguita combinando la potenza dei runtime di realtà mista esistenti, come il [mapping spaziale](spatial-mapping.md) altamente accurato ma meno strutturato e i nuovi runtime basati su intelligenza artificiale. Combinando queste tecnologie, la comprensione della scena genera rappresentazioni di ambienti 3D simili a quelle che potrebbero essere state usate nei Framework, ad esempio Unity o ARKit/ARCore. Il punto di ingresso comprensione della scena inizia con un Observer della scena, che viene chiamato dall'applicazione per calcolare una nuova scena. Attualmente, la tecnologia può generare tre categorie di oggetti distinti ma correlati: 

* Mesh di ambiente impermeabile semplificate che deducono la struttura di spazio planare senza confusione
* Aree del piano per la selezione host chiamata quad
* Uno snapshot della mesh di [mapping spaziale](spatial-mapping.md) che è allineato con i quad/dati stagni che emergiamo

![Mesh di mapping spaziale, superfici planari con etichetta, mesh impermeabile](images/SUScenarios.png)

Questo documento ha lo scopo di fornire una panoramica dello scenario e di chiarire la relazione tra la conoscenza della scena e la condivisione di mapping spaziale.

## <a name="developing-with-scene-understanding"></a>Sviluppo con comprensione della scena

Questo articolo serve solo per introdurre la scena per comprendere il runtime e i concetti. Se si sta cercando la documentazione su come sviluppare con la comprensione della scena, è possibile che si siano interessati agli articoli seguenti:

[Panoramica dell'SDK per la comprensione della scena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

È possibile scaricare l'app di esempio per informazioni sulla scena dal sito GitHub di esempio:

[Esempio di comprensione della scena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Se non si ha un dispositivo e si vuole accedere a scene di esempio per provare a comprendere la scena, sono disponibili alcune scene nella cartella asset di esempio:

[Scene di esempio sulla comprensione della scena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

Per informazioni dettagliate sullo sviluppo con la comprensione della scena, vedere la pagina relativa alla [Panoramica della panoramica dell'SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) .

### <a name="sample"></a>Esempio

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Informazioni sulle scene</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>Scenari di utilizzo comuni

![Illustrazioni degli scenari comuni di utilizzo del mapping spaziale: posizionamento, occlusione, fisica e navigazione](images/sm-concepts-1000px.png)<br>
*Scenari comuni di utilizzo del mapping spaziale: posizionamento, occlusione, fisica e navigazione.*

<br>

Molti degli scenari principali per le applicazioni compatibili con l'ambiente possono essere risolti sia dal mapping spaziale che dalla comprensione della scena. Questi scenari principali includono posizionamento, occlusione, fisica e così via. Una differenza fondamentale tra la comprensione della scena e il mapping spaziale è un compromesso tra precisione massima e latenza alla struttura e alla semplicità. Se l'applicazione richiede la latenza più bassa possibile e i triangoli mesh a cui si vuole accedere solo, usare direttamente il mapping spaziale. Se si sta eseguendo un'elaborazione di livello superiore, è possibile passare al modello di comprensione della scena in quanto dovrebbe fornire un superset di funzionalità. Sarà sempre possibile accedere ai dati di mapping spaziali più completi e accurati perché la comprensione della scena fornisce uno snapshot della mesh di mapping spaziale come parte della relativa rappresentazione.

Le sezioni seguenti rivisitano gli scenari di mapping spaziale principali nel contesto della nuova scena Understanding SDK.

### <a name="placement"></a>Selezione host

La comprensione della scena fornisce nuovi costrutti progettati per semplificare gli scenari di posizionamento. Una scena può calcolare le primitive denominate SceneQuads, che descrivono le superfici piane in cui è possibile posizionare gli ologrammi. SceneQuads sono stati progettati intorno al posizionamento e descrivono una superficie 2D e forniscono un'API per la selezione host su tale superficie. In precedenza, quando si utilizzava la mesh triangolare per eseguire la selezione host, era necessario analizzare tutte le aree del quad ed eseguire operazioni di riempimento/post-elaborazione dei fori per identificare posizioni valide per la posizione degli oggetti. Questa operazione non è sempre necessaria con i quad, perché la scena che comprende il runtime deduce quali aree quadre non sono state analizzate e invalida le aree che non fanno parte della superficie.

:::row:::
    :::column:::
       ![SceneQuads con inferenza disabilitata, acquisizione delle aree di posizionamento per le aree analizzate.](images/SUQuads.png)<br>
       **Image #1** -SceneQuads con inferenza disabilitata, acquisizione delle aree di posizionamento per le aree analizzate.
    :::column-end:::
        :::column:::
       ![Quad con inferenza abilitata, la selezione host non è più limitata alle aree analizzate.](images/SUWatertight.png)<br>
        **Image #2** -quad con inferenza abilitata, la selezione host non è più limitata alle aree analizzate.
    :::column-end:::
:::row-end:::

<br>


Se l'applicazione intende inserire ologrammi 2D o 3D in strutture rigide dell'ambiente, la semplicità e la praticità di SceneQuads per la selezione host sono preferibili al calcolo di queste informazioni dalla mesh di [mapping spaziale](spatial-mapping.md) . Per ulteriori informazioni su questo argomento, vedere la sezione [informazioni di riferimento sull'SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

**Nota** Per il codice di posizionamento legacy che dipende dalla mesh di mapping spaziale, è possibile calcolare la mesh di mapping spaziale insieme a SceneQuads impostando l'impostazione di EnableWorldMesh. Se l'API per la comprensione della scena non soddisfa i requisiti di latenza dell'applicazione, si consiglia di continuare a usare l' [API di mapping spaziale](spatial-mapping.md#placement).

### <a name="occlusion"></a>Occlusione

L' [occlusione del mapping spaziale](spatial-mapping.md#occlusion) rimane il modo meno latente per acquisire lo stato in tempo reale dell'ambiente. Sebbene ciò possa risultare utile per fornire l'occlusione in scenari estremamente dinamici, è consigliabile prendere in considerazione la comprensione della scena per l'occlusione per diversi motivi. Se si usa la mesh di mapping spaziale generata dalla comprensione della scena, è possibile richiedere dati dal mapping spaziale che non verranno archiviati nella cache locale e che non sono disponibili nelle API di percezione. L'uso del mapping spaziale per l'occlusione insieme alle mesh stagne fornirà un valore aggiuntivo, in particolare il completamento della struttura della stanza non analizzata.

Se i requisiti possono tollerare un aumento della latenza della comprensione della scena, gli sviluppatori di applicazioni devono prendere in considerazione l'uso della scena per comprendere la mesh stermetica e la mesh di mapping spaziale in Unison con le rappresentazioni planari Questo potrebbe offrire uno scenario "migliore di entrambi i mondi", in cui l'occlusione stagna semplificata è sposata con una geometria non piana più precisa che fornisce le mappe di occlusione più realistiche possibili.

### <a name="physics"></a>Fisica

La comprensione della scena genera maglie stagne che compongono lo spazio con la semantica, in particolare per rispondere a molte limitazioni per la fisica che i mesh di mapping spaziale impongono. Le strutture stagne assicurano che i cast dei raggi fisici vengano sempre raggiunti e la scomposizione semantica consente la generazione più semplice di mesh NAV per la navigazione interna. Come descritto nella sezione relativa all' [occlusione](#occlusion), la creazione di una scena con EnableSceneObjectMeshes e EnableWorldMesh produrrà la mesh più fisicamente completa possibile. La proprietà stagne della mesh dell'ambiente impedisce che gli hit test riscontrino le superfici. I dati di rete garantiscono che la fisica interagisca con tutti gli oggetti nella scena e non solo con la struttura della stanza.

### <a name="navigation"></a>Navigazione

Le mesh planari decomposte dalla classe semantica sono costrutti ideali per la pianificazione della navigazione e del percorso, semplificando molti dei problemi descritti nella panoramica dello [spostamento del mapping spaziale](spatial-mapping.md#navigation) . Gli oggetti SceneMesh calcolati nella scena sono decomposti dal tipo di superficie, assicurando che la generazione della mesh NAV sia limitata alle superfici che possono essere esaminate. A causa della semplicità, la generazione della mesh NAV dinamica nei motori 3D, ad esempio Unity, è raggiungibile a seconda dei requisiti in tempo reale.

La generazione di mesh NAV accurate attualmente richiede la post-elaborazione, vale a dire che le applicazioni devono ancora proiettare occluders in base al piano per garantire che la navigazione non passi attraverso confusione/tabelle e così via. Il modo più preciso per eseguire questa operazione consiste nel proiettare i dati della mesh globale, che vengono forniti se la scena viene calcolata con il flag EnableWorldMesh.

### <a name="visualization"></a>Visualizzazione

Sebbene la [visualizzazione del mapping spaziale](spatial-mapping.md#visualization) possa essere usata per il feedback in tempo reale dell'ambiente, esistono molti scenari in cui la semplicità degli oggetti planari e stagni garantisce maggiore prestazioni o qualità visiva. Le tecniche di proiezione Shadow e di base descritte con il mapping spaziale possono essere più gradevoli se proiettate sulle superfici planari fornite da quad o dalla mesh impermeabile piana. Ciò vale soprattutto per gli ambienti e gli scenari in cui l'analisi preliminare completa non è ottimale perché la scena si dedurrà e gli ambienti completi e i presupposti planari riducono al minimo gli artefatti.

Inoltre, il numero totale di superfici restituite dal mapping spaziale è limitato dalla cache spaziale interna, mentre la versione di comprensione della scena della mesh di mapping spaziale può accedere ai dati di mapping spaziali non memorizzati nella cache. Per questo motivo, la comprensione della scena è più adatta per l'acquisizione di rappresentazioni di mesh per spazi più grandi (ad esempio, più grandi di una singola stanza) per la visualizzazione o per un'ulteriore elaborazione di mesh. La mesh globale restituita con EnableWorldMesh avrà un livello di dettaglio coerente, che può produrre una visualizzazione più gradevole se ne viene eseguito il rendering come wireframe.

### <a name="see-also"></a>Vedere anche

* [Scenario di comprensione dell'SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [Mapping spaziale](spatial-mapping.md)
