---
title: Informazioni sulle scene
description: Informazioni su come sviluppare con la comprensione della scena per HoloLens, inclusi l'SDK, le funzionalità e gli scenari di utilizzo comuni.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, Windows Mixed Reality, Unity, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, occlusione, SDK
ms.openlocfilehash: 06a4fdb6f3ad777c47151950acbd4ccdec9935ca
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143592"
---
# <a name="scene-understanding"></a>Informazioni sulle scene

La comprensione della scena offre agli sviluppatori di realtà mista una rappresentazione dell'ambiente strutturata di alto livello progettata per rendere intuitivo lo sviluppo per applicazioni con consapevolezza ambientale. La comprensione della scena combina la potenza dei runtime di realtà mista esistenti, ad esempio il mapping spaziale estremamente accurato ma meno [strutturato](spatial-mapping.md) e i nuovi runtime di intelligenza artificiale. Combinando queste tecnologie, Scene Understanding genera rappresentazioni di ambienti 3D simili a quelle usate in framework come Unity o ARKit/ARCore. Il punto di ingresso di comprensione della scena inizia con un osservatore di scena, chiamato dall'applicazione per calcolare una nuova scena. Oggi la tecnologia può generare 3 categorie di oggetti distinte ma correlate:

* Mesh dell'ambiente a tenuta d'acqua semplificate che deduceno la struttura planare della stanza senza confusione
* Aree del piano per il posizionamento chiamate quad
* Snapshot della mesh [di mapping](spatial-mapping.md) spaziale in linea con i dati Quad/Watertight che vengono emersi

![Mesh di mapping spaziale, superfici planari etichettate, mesh stagna](images/SUScenarios.png)

Questo documento ha lo scopo di fornire una panoramica dello scenario e di chiarire la relazione che la comprensione della scena e il mapping spaziale condividono. Se si desidera vedere Scene Understanding in azione, vedere la demo video [Designing Holograms - Spatial Awareness (Progettazione di ologrammi - Consapevolezza]() spaziale) di seguito:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="developing-with-scene-understanding"></a>Sviluppo con la comprensione della scena

Questo articolo illustra solo il runtime e i concetti di Scene Understanding. Se si sta cercando documentazione su come sviluppare con Scene Understanding, è possibile che si sia interessati agli articoli seguenti:

[Panoramica di Scene Understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

È possibile scaricare l'app Scene Understanding Sample dal sito GitHub di esempio:

[Esempio di comprensione della scena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Se non si dispone di un dispositivo e si vuole accedere a scene di esempio per provare Scene Understanding, sono presenti scene nella cartella asset di esempio:

[Scene di esempio per la comprensione della scena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

Per informazioni dettagliate specifiche sullo sviluppo con Scene Understanding, vedere la documentazione [panoramica di Scene Understanding SDK.](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
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

![Illustrazioni di scenari comuni di utilizzo del mapping spaziale: posizionamento, occlusione, fisica e navigazione](images/sm-concepts-1000px.png)<br>
*Scenari comuni di utilizzo del mapping spaziale: posizionamento, occlusione, fisica e navigazione.*

<br>

Molti degli scenari di base per le applicazioni con supporto ambientale possono essere affrontati sia dal mapping spaziale che dalla comprensione della scena. Questi scenari principali includono posizionamento, occlusione, fisica e così via. Una differenza fondamentale tra la comprensione della scena e il mapping spaziale è un compromesso tra accuratezza massima e latenza alla struttura e alla semplicità. Se l'applicazione richiede la latenza più bassa possibile e i triangoli mesh a cui si vuole accedere solo a cui si vuole accedere, usare direttamente Mapping spaziale. Se si sta eseguendo un'elaborazione di livello superiore, è possibile passare al modello di comprensione della scena perché dovrebbe fornire un superset di funzionalità. Sarà sempre possibile accedere ai dati di mapping spaziali più completi e accurati possibili perché la comprensione della scena fornisce uno snapshot della mesh di mapping spaziale come parte della relativa rappresentazione.

Le sezioni seguenti rivisitano gli scenari di mapping spaziale di base nel contesto del nuovo SDK di comprensione della scena.

### <a name="placement"></a>Selezione host

La comprensione della scena offre nuovi costrutti progettati per semplificare gli scenari di posizionamento. Una scena può calcolare primitive denominate SceneQuads, che descrivono superfici piatte su cui è possibile inserire ologrammi. SceneQuads è stato progettato in base al posizionamento e descrive una superficie 2D e fornisce un'API per il posizionamento su tale superficie. In precedenza, quando si usava la mesh triangolare per eseguire il posizionamento, era necessario analizzare tutte le aree del quad ed eseguire il riempimento/post-elaborazione dei fori per identificare le posizioni buone per il posizionamento degli oggetti. Questo non è sempre necessario con i quad, perché il runtime di comprensione della scena deduce quali aree quad non sono state analizzate e invalida le aree che non fanno parte della superficie.

:::row:::
    :::column:::
       ![SceneQuads con inferenza disabilitata, che acquisisce le aree di posizionamento per le aree analizzate.](images/SUQuads.png)<br>
       **Immagine #1:** SceneQuads con inferenza disabilitata, che acquisisce le aree di posizionamento per le aree digitalizzate.
    :::column-end:::
        :::column:::
       ![Quad con inferenza abilitata, il posizionamento non è più limitato alle aree analizzate.](images/SUWatertight.png)<br>
        **Immagine #2:** i quad con inferenza abilitata, il posizionamento non è più limitato alle aree digitalizzate.
    :::column-end:::
:::row-end:::

<br>


Se l'applicazione intende posizionare ologrammi 2D o 3D in strutture rigide dell'ambiente, la semplicità e la praticità di SceneQuads per il posizionamento sono preferibili al calcolo di queste informazioni dalla mesh di [mapping](spatial-mapping.md) spaziale. Per altre informazioni su questo argomento, vedere informazioni [di riferimento su Scene Understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

**Nota** Per il codice di posizionamento legacy che dipende dalla mesh di mapping spaziale, la mesh di mapping spaziale può essere calcolata insieme a SceneQuads impostando EnableWorldMesh. Se l'API di comprensione della scena non soddisfa i requisiti di latenza dell'applicazione, è consigliabile continuare a usare [l'API di mapping spaziale](spatial-mapping.md#placement).

### <a name="occlusion"></a>Occlusione

[L'occlusione del mapping](spatial-mapping.md#occlusion) spaziale rimane il modo meno latente per acquisire lo stato in tempo reale dell'ambiente. Anche se questo può essere utile per fornire l'occlusione in scene altamente dinamiche, è consigliabile prendere in considerazione la comprensione della scena per diversi motivi. Se si usa la mesh di mapping spaziale generata da Scene Understanding, è possibile richiedere dati dal mapping spaziale che non vengono archiviati nella cache locale e non sono disponibili dalle API di percezione. L'uso del mapping spaziale per l'occlusione insieme alle mesh a ermetico fornirà un valore aggiuntivo, in particolare il completamento della struttura della stanza non in analisi.

Se i requisiti possono tollerare l'aumento della latenza di comprensione della scena, gli sviluppatori di applicazioni devono prendere in considerazione l'uso della mesh di comprensione della scena e della mesh di mapping spaziale in unisono con rappresentazioni planari. Questo offre uno scenario "migliore di entrambi i mondo", in cui l'occlusione semplificata con occlusione stagnante è ideale con una geometria nonplanare più fine che offre le mappe di occlusione più realistiche possibili.

### <a name="physics"></a>Fisica

La comprensione della scena genera mesh stazionate che scompongono lo spazio con la semantica, in particolare per affrontare molte limitazioni alla fisica imposte dalla mesh di mapping spaziale. Le strutture a ermetica assicurano che i ray cast fisici raggino sempre e la scomposizione semantica consente una generazione più semplice di mesh di spostamento per la navigazione all'interno. Come descritto nella sezione relativa [all'occlusione,](#occlusion)la creazione di una scena con EnableSceneObjectMeshes e EnableWorldMesh produrrà la mesh fisicamente più completa possibile. La proprietà stagna della mesh dell'ambiente impedisce agli hit test di non riuscire a superare le superfici. I dati della mesh garantiranno che la fisica interagisca con tutti gli oggetti nella scena e non solo con la struttura della stanza.

### <a name="navigation"></a>Spostamento

Le mesh planari scomposte per classe semantica sono costrutti ideali per la pianificazione della navigazione e del percorso, per risolvere molti dei problemi descritti in Panoramica della navigazione [con mapping](spatial-mapping.md#navigation) spaziale. Gli oggetti SceneMesh calcolati nella scena sono de-composti in base al tipo di superficie, assicurando che la generazione della mesh di spostamento sia limitata alle superfici su cui è possibile andare. Grazie alla semplicità delle strutture del piano, la generazione dinamica della mesh di spostamento in motori 3D come Unity è raggiungibile a seconda dei requisiti in tempo reale.

La generazione di mesh di spostamento accurate attualmente richiede ancora la post-elaborazione. In altre informazioni, le applicazioni devono comunque proiettare occluder sul piano per garantire che la navigazione non passi attraverso confusione/tabelle e così via. Il modo più accurato per eseguire questa operazione è proiettare i dati della mesh mondiale, che vengono forniti se la scena viene calcolata con il flag EnableWorldMesh.

### <a name="visualization"></a>Visualizzazione

Anche [se la](spatial-mapping.md#visualization) visualizzazione del mapping spaziale può essere usata per il feedback in tempo reale dell'ambiente, esistono molti scenari in cui la semplicità degli oggetti planari e stagnati offre prestazioni o qualità visiva maggiori. Le tecniche di proiezione dell'ombreggiatura e di messa a terra descritte usando il mapping spaziale possono essere più gradevoli se proiettate sulle superfici planari fornite da Quad o dalla mesh a ermetico planare. Ciò vale soprattutto per gli ambienti/scenari in cui la pre-analisi approfondita non è ottimale perché la scena dedurrà e gli ambienti completi e i presupposti planari ridurranno al minimo gli artefatti.

Inoltre, il numero totale di superfici restituite da Mapping spaziale è limitato dalla cache spaziale interna, mentre la versione di Scene Understanding della mesh mapping spaziale può accedere ai dati di mapping spaziale non memorizzati nella cache. Per questo, la comprensione della scena è più adatta all'acquisizione di rappresentazioni mesh per spazi più grandi (ad esempio, più grandi di una singola stanza) per la visualizzazione o l'ulteriore elaborazione della mesh. La mesh globale restituita con EnableWorldMesh avrà in tutto un livello di dettaglio coerente, che può produrre una visualizzazione più gradevole se sottoposta a rendering come wireframe.

### <a name="see-also"></a>Vedere anche

* [SDK di comprensione della scena](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [Mapping spaziale](spatial-mapping.md)