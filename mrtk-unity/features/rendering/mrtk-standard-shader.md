---
title: MRTK Standard Shader
description: Documentazione per MRTKStandardShader
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, material shader
ms.openlocfilehash: 8b570ebb023305cecbeca16b32832417a3f57cce
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145115"
---
# <a name="mrtk-standard-shader"></a>MRTK Standard Shader

![Esempi di shader standard](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

Il sistema di ombreggiatura standard MRTK usa un singolo shader flessibile in grado di ottenere oggetti visivi simili allo shader standard di Unity, implementare i principi [di Fluent Design System](https://www.microsoft.com/design/fluent/) e mantenere le prestazioni nei dispositivi di realtà mista.

## <a name="example-scenes"></a>Scene di esempio

È possibile trovare gli esempi di materiale shader nella **scena MaterialGallery** in `MRTK/Examples/Demos/StandardShader/Scenes/` . Tutti i materiali in questa scena usano lo shader MRTK/Standard.

![Raccolta di materiali](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

È possibile trovare una scena di confronto per confrontare e testare lo shader MRTK/Standard rispetto all'esempio di shader Unity/Standard nella scena **StandardMaterialComparison** in `MRTK/Examples/Demos/StandardShader/Scenes/` .

![Confronto dei materiali](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Architettura

Il sistema di ombreggiatura MRTK/Standard è un "uber shader" che usa la funzionalità di variante del programma shader di [Unity](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) per generare automaticamente codice shader ottimale in base alle proprietà del materiale. Quando un utente seleziona le proprietà dei materiali nel controllo dei materiali, comporta solo un costo in termini di prestazioni per le funzionalità abilitate.

## <a name="material-inspector"></a>Controllo materiale

Esiste un controllo materiale personalizzato per lo shader MRTK/Standard denominato [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) . Il controllo abilita/disabilita automaticamente le funzionalità dello shader, in base alla selezione dell'utente e consente di configurare lo stato di rendering. Per altre informazioni su ogni funzionalità, **passare il mouse su ogni proprietà nell'editor di Unity per visualizzare una descrizione comando.**

![Controllo materiale](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

La prima parte del controllo controlla lo stato di rendering del materiale. *La modalità di* rendering determina quando e come verrà eseguito il rendering di un materiale. Lo scopo dello shader MRTK/Standard è rispecchiare le modalità di [rendering disponibili nello shader Unity/Standard.](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) Lo shader MRTK/Standard include anche una modalità di rendering *additiva* e una *modalità* di rendering personalizzata per il controllo utente completo.

| Modalità di rendering |         Descrizione                                                       |
|----------------|---------------------------------------------------------------------------|
| Opaco         | (Impostazione predefinita) Adatto per normali oggetti solidi senza aree trasparenti.    |
| Ritaglio         | Consente la creazione di effetti trasparenti con bordi rigidi tra le aree opache e trasparenti. In questa modalità non sono presenti aree semitrasparenti, la trama è opaca al 100% o invisibile. Ciò è utile quando si usa la trasparenza per creare la forma dei materiali, ad esempio la verdeggiante. |
| Dissolvenza           | Consente ai valori di trasparenza di dissolvere completamente un oggetto, incluse eventuali evidenziazioni speculari o riflessi. Questa modalità è utile se si vuole aggiungere un'animazione a un oggetto che sbiade o esce. Non è adatto per il rendering di materiali trasparenti realistici, ad esempio plastica trasparente o vetro, perché anche i riflessi e le evidenziazioni verranno sfumare. |
| Modalità trasparente    | Adatto per il rendering di materiali trasparenti realistici, ad esempio plastica trasparente o vetro. In questa modalità, il materiale stesso accetta valori di trasparenza (in base al canale alfa della trama e all'alfa del colore della tinta). I riflessi e le evidenziazioni di illuminazione, tuttavia, rimarranno visibili con la massima chiarezza, come nel caso di materiali reali trasparenti. |
| Additive       | Abilita una modalità di fusione additiva, che somma il colore pixel precedente con il colore pixel corrente. Si tratta della modalità di trasparenza preferita per evitare problemi di ordinamento della trasparenza.     |
| Personalizzato         | Consente di controllare manualmente ogni aspetto della modalità di rendering. Solo per utilizzo avanzato.   |

![Modalità di rendering](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| Modalità Cull |             Descrizione                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Off       | Disabilita l'culling dei viso. L'opzione Culling deve essere impostata su Off solo quando è necessaria una mesh a due lati.                                                                                        |
| Front     | Abilita l'culling del viso anteriore.                                                                                                                                                        |
| Indietro      | (Impostazione predefinita) Abilita [l'opzione back face culling](https://en.wikipedia.org/wiki/Back-face_culling). L'culling del viso posteriore deve essere abilitato il più spesso possibile per migliorare le prestazioni di rendering. |

## <a name="performance"></a>Prestazioni

Uno dei principali vantaggi dell'uso dello shader STANDARD MRTK rispetto allo shader standard Unity è quello delle prestazioni. Lo shader STANDARD MRTK è estendibile per usare solo le funzionalità abilitate. Tuttavia, è stato scritto anche lo shader MRTK Standard per offrire risultati estetici simili a quelli dello shader Unity Standard, ma a un costo molto inferiore. Un modo semplice per confrontare le prestazioni dello shader è il numero di operazioni che devono essere eseguite nella GPU. Naturalmente, la grandezza dei calcoli può variare in base alle funzionalità abilitate e ad altre configurazioni di rendering. In generale, tuttavia, lo shader MRTK Standard esegue un calcolo significativamente inferiore rispetto allo shader Unity Standard.

Esempio di statistiche dello shader Unity Standard

![Statistiche shader standard di Unity](../images/performance/UnityStandardShader-Stats.PNG)

Esempio di statistiche dello shader STANDARD MRTK

![Statistiche dello shader standard MRTK](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> Questi risultati possono essere generati selezionando e visualizzando un [asset shader](https://docs.unity3d.com/Manual/class-Shader.html) nel controllo Unity, quindi facendo clic sul pulsante *Compila e* mostra codice.

## <a name="lighting"></a>Luce

MrTK/Standard usa una semplice approssimazione per l'illuminazione. Poiché questo shader non calcola la correttezza fisica e la conservazione dell'energia, il rendering viene eseguito in modo rapido ed efficiente. Blinn-Phong è la tecnica di illuminazione principale, che si combina con Fresnel e l'illuminazione basata su immagini per ottenere un'illuminazione fisica approssimativa. Lo shader supporta le tecniche di illuminazione seguenti:

### <a name="directional-light"></a>Luce direzionale

Lo shader rispetterà la direzione, il colore e l'intensità della prima luce direzionale Unity nella scena (se abilitata). Le luci a punti dinamiche, le luci spot o qualsiasi altra luce unity non verranno considerate nell'illuminazione in tempo reale.

### <a name="spherical-harmonics"></a>Armonici sferici

Lo shader userà Probe di luce per approssimare le luci nella scena usando [Spherical Armoniche,](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)se abilitata. I calcoli armonici sferici vengono eseguiti per vertice per ridurre i costi di calcolo.

### <a name="lightmapping"></a>Mapping di luce

Per l'illuminazione statica, lo shader rispetterà le mappe di luce create dal [sistema Lightmapping di](https://docs.unity3d.com/Manual/Lightmapping.html)Unity. È sufficiente contrassegnare il renderer come statico (o statico lightmap) per usare le mappe di luce.

### <a name="hover-light"></a>Luce del passaggio del mouse

* Vedere [Luce al passaggio del mouse](hover-light.md)

### <a name="proximity-light"></a>Luce di prossimità

* Vedere [Luce di prossimità](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>Supporto della pipeline di rendering lightweight scriptable

MrTK contiene un percorso di aggiornamento per consentire agli sviluppatori di usare la pipeline di rendering lightweight scriptable (LWRP) di Unity con shader MRTK. Testato nel pacchetto Unity 2019.1.1f1 e Lightweight RP 5.7.2. o istruzioni per iniziare a usare LWRP, vedere [questa pagina.](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)

Per eseguire l'aggiornamento di MRTK, selezionare: **Mixed Reality Toolkit -> Utilities -> Upgrade MRTK Standard Shader for Lightweight Render Pipeline**

![Aggiornamento lwrp](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

Dopo l'aggiornamento, lo shader MRTK/Standard verrà modificato e tutti i materiali magenta (errore shader) devono essere corretti. Per verificare che l'aggiornamento sia stato eseguito correttamente, controllare nella console asset **aggiornati/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader** per l'uso con la pipeline di rendering leggera.

## <a name="ugui-support"></a>Supporto UGUI

Il sistema di ombreggiatura di MRTK Standard funziona con il sistema di interfaccia utente [incorporato di](https://docs.unity3d.com/Manual/UISystem.html)Unity. Nei componenti dell'interfaccia utente di Unity, la matrice unity_ObjectToWorld non è la matrice di trasformazione della trasformazione locale in cui si trova il componente Grafico, ma quella del canvas padre. Molti effetti shader MRTK/Standard richiedono che la scala degli oggetti sia nota. Per risolvere questo problema, archivia le informazioni di ridimensionamento in attributi [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) del canale UV durante la costruzione della mesh dell'interfaccia utente.

Si noti che quando si usa un componente immagine unity, è consigliabile specificare "Nessuno (Sprite)" per l'immagine di origine per impedire all'interfaccia utente di Unity di generare vertici aggiuntivi.

Un canvas all'interno di MRTK richiederà l'aggiunta di [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) un quando è necessario:

![Ridimensionare l'effetto mesh](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>Combinatore di trame

Per migliorare la parità con lo shader standard Unity per pixel, è possibile controllare tutti i valori di uniformità, emissive e occlusione tramite la creazione di un pacchetto [di canali.](http://wiki.polycount.com/wiki/ChannelPacking) Esempio:

![Esempio di mappa dei canali](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

Quando si usa la creazione di un pacchetto di canali, è sufficiente campionare e caricare una trama in memoria anziché quattro trame separate. Quando si scrivono le mappe trame in un programma, ad esempio Azzarre o Photoshop, è possibile imballarle come segue:

| Channel | Proprietà             |
|---------|----------------------|
| Red     | Metallici             |
| Green   | Occlusione            |
| Blu    | Emissione (gradazioni di grigio) |
| Alfa   | Scorrevolezza           |

In caso contrario, è possibile usare lo strumento combinatore di trame MRTK. Per aprire lo strumento, selezionare: **Mixed Reality Toolkit -> Utilities -> Texture Combiner (Mixed Reality Toolkit -> Utilities -> Texture Combiner** (Combinatore di trame) che aprirà la finestra seguente:

![Esempio di combinatore di trame](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Questa finestra può essere compilata automaticamente selezionando uno shader Unity Standard e facendo clic su "Autopopulate from Standard Material" (Popolamento automatico da materiale standard). In caso contrario, è possibile specificare manualmente una trama (o un valore costante) per ogni canale rosso, verde, blu o alfa. La combinazione di trame è accelerata dalla GPU e non richiede che la trama di input sia accessibile alla CPU.

## <a name="additional-feature-documentation"></a>Documentazione aggiuntiva delle funzionalità

Di seguito sono riportati dettagli aggiuntivi su una serie di dettagli delle funzionalità disponibili con lo shader MRTK/Standard.

### <a name="primitive-clipping"></a>Ritaglio primitivo

![ritaglio primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* Vedere [Primitiva di ritaglio](clipping-primitive.md)

### <a name="mesh-outlines"></a>Strutture mesh

Molte tecniche di struttura della mesh vengono eseguite usando una tecnica [di post-elaborazione.](https://docs.unity3d.com/Manual/PostProcessingOverview.html) La post-elaborazione offre un'ottima qualità, ma può essere proibitivamente costosa in molti dispositivi di realtà mista. È possibile trovare una scena che illustra l'uso delle strutture mesh nella  **scena OutlineExamples in** `MRTK/Examples/Demos/StandardShader/Scenes/` .

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) e [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) possono essere usati per eseguire il rendering di un contorno intorno a un renderer mesh. L'abilitazione di questo componente introduce un passaggio di rendering aggiuntivo dell'oggetto da delineare, ma è progettato per essere eseguito in modo performante nei dispositivi mobili di realtà mista e non usa alcun processo post. Le limitazioni di questo effetto includono che non funziona correttamente sugli oggetti che non sono a tenuta stagna (o devono essere a due lati) e possono verificarsi problemi di ordinamento della profondità su oggetti sovrapposti.

I comportamenti della struttura sono progettati per essere usati in combinazione con lo shader MRTK/Standard. I materiali di contorno sono in genere un colore non illuminato a tinta unita, ma possono essere configurati per ottenere un'ampia gamma di effetti. La configurazione predefinita di un materiale di struttura è la seguente:

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. Scrittura profondità: deve essere disabilitata per i materiali di struttura per assicurarsi che la struttura non impedirà il rendering di altri oggetti.
2. Estrusione vertice: deve essere abilitata per il rendering della struttura.
3. Usa normali smussati: questa impostazione è facoltativa per alcune mesh. L'estrusione si verifica spostando un vertice lungo una normale vertice, in alcune mesh estruso lungo le normali predefinite causeranno discontinuità nella struttura. Per correggere queste discontinuità, è possibile selezionare questa casella per usare un altro set di normali smussate generate da [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) è un componente che può essere usato per generare automaticamente normali smussate su una mesh. Questo metodo raggruppa i vertici in una mesh che condividono la stessa posizione nello spazio, quindi esegue la media delle normali di tali vertici. Questo processo crea una copia della mesh sottostante e deve essere usato solo quando necessario.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. Normali uniformi generate tramite [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) .
2. Vengono usate le normali predefinite. Si notino gli artefatti intorno agli angoli del cubo.

### <a name="stencil-testing"></a>Test degli stencil

Supporto di test degli stencil configurabile per ottenere un'ampia gamma di effetti. Ad esempio i portali:

![test stencil](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>Supporto dei colori con istanze

Supporto dei colori con istanze per offrire migliaia di mesh con istanze GPU proprietà del materiale univoche:

![proprietà con istanze](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Mapping triplanar

Il mapping triplanar è una tecnica per la trama di una mesh a livello di codice. Spesso usato in terreno, mesh senza UV o difficile da annullare il wrapping delle forme. Questa implementazione supporta la proiezione di tutto il mondo o dello spazio locale, la specifica di smussamento della fusione e il normale supporto della mappa. Si noti che ogni trama usata richiede 3 campioni di trama, quindi usare solo in situazioni critiche per le prestazioni.

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>Estrusione vertice

Estrusione dei vertici nello spazio mondiale. Utile per visualizzare i volumi di delimitazione estruso o le transizioni di mesh in/out.

![scala mappa normale 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>Varie

Casella di controllo per controllare le ottimizzazioni di albedo. Poiché le operazioni albedo di ottimizzazione vengono disabilitate quando non viene specificata alcuna trama albedo. Ciò è utile per controllare il [caricamento remoto delle trame.](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)

È sufficiente selezionare questa casella:

![assegnazione albedo](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

Sono supportate trame di ritaglio per pixel, anti aliasing basato sul bordo locale e scalabilità normale della mappa.

![scala mappa normale 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>Vedi anche

* [Interagibile](../ux-building-blocks/interactable.md)
* [Luce del passaggio del mouse](hover-light.md)
* [Luce di prossimità](proximity-light.md)
* [Primitiva di ritaglio](clipping-primitive.md)
