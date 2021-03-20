---
title: MRTKStandardShader
description: Documentazione per MRTKStandardShader
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Material shader
ms.openlocfilehash: 608710296ec9bcf9dcb8a7672cbe356c3b1a0603
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685214"
---
# <a name="mrtk-standard-shader"></a>Shader standard MRTK

![Esempi di shader standard](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

Il sistema di ombreggiatura standard MRTK usa un unico shader flessibile che può ottenere oggetti visivi simili allo shader standard di Unity, implementare i principi del [sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/) e rimanere efficienti nei dispositivi a realtà mista.

## <a name="example-scenes"></a>Scene di esempio

È possibile trovare gli esempi di materiale dello shader nella scena **MaterialGallery** in `MRTK/Examples/Demos/StandardShader/Scenes/` . Tutti i materiali in questa scena utilizzano lo shader MRTK/standard.

![Raccolta materiali](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

È possibile trovare una scena di confronto per confrontare e testare lo shader MRTK/standard rispetto all'esempio di Unity/standard shader nella scena **StandardMaterialComparison** sotto `MRTK/Examples/Demos/StandardShader/Scenes/` .

![Confronto materiali](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Architettura

Il sistema di ombreggiatura MRTK/standard è un "uber shader" che usa la [funzionalità variant del programma shader di Unity](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) per generare automaticamente il codice dello shader ottimale in base alle proprietà del materiale. Quando un utente seleziona le proprietà del materiale in Material Inspector, comporta solo il costo delle prestazioni per le funzionalità abilitate.

## <a name="material-inspector"></a>Controllo materiale

Un controllo Material personalizzato esiste per lo shader MRTK/standard chiamato [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) . Il controllo Abilita/Disabilita automaticamente le funzionalità dello shader, in base alla selezione dell'utente e ai collaboratori per la configurazione dello stato di rendering. Per altre informazioni su ogni funzionalità **, passare il puntatore del mouse su ogni proprietà nell'editor di Unity per una descrizione comando.**

![Controllo materiale](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

La prima parte del controllo Controlla lo stato di rendering del materiale. La *modalità di rendering* determina quando e come verrà eseguito il rendering di un materiale. L'obiettivo dello shader MRTK/standard è quello di eseguire il mirroring delle [modalità di rendering disponibili nello shader Unity/standard](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html). Lo shader MRTK/standard include anche una modalità di rendering *additiva* e la modalità di rendering *personalizzata* per il controllo utente completo.

| Modalità di rendering |         Descrizione                                                                                                                                                                                                                                                                                                                                                           |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Opaco         | Predefinita Adatto per oggetti solidi normali senza aree trasparenti.                                                                                                                                                                                                                                                                                             |
| Ritaglio         | Consente la creazione di effetti trasparenti con bordi rigidi tra le aree opache e trasparenti. In questa modalità non sono presenti aree semitrasparenti, la trama è opaca del 100% o invisibile. Questa operazione è utile quando si usa la trasparenza per creare la forma di materiali, ad esempio la vegetazione.                                                              |
| Dissolvenza           | Consente ai valori di trasparenza di dissolvere completamente un oggetto, incluse le evidenziazioni speculari o i riflessi che può avere. Questa modalità è utile se si desidera animare il dissolvenza di un oggetto. Non è adatto per il rendering di materiali trasparenti realistici, ad esempio Clear Plastic o Glass, perché i riflessi e le evidenziazioni verranno anche sbiaditi. |
| Modalità trasparente    | Adatto per il rendering di materiali trasparenti realistici, ad esempio Clear Plastic o Glass. In questa modalità, il materiale stesso prenderà i valori di trasparenza (in base al canale alfa della trama e all'alfa del colore della tinta). Tuttavia, i riflessi e le evidenziazioni dell'illuminazione rimarranno visibili con chiarezza completa, come nel caso di materiali trasparenti reali. |
| Additive       | Abilita una modalità di fusione additiva, che somma il colore del pixel precedente con il colore del pixel corrente. Si tratta della modalità di trasparenza preferita per evitare problemi di ordinamento della trasparenza.                                                                                                                                                                                  |
| Personalizzato         | Consente di controllare manualmente ogni aspetto della modalità di rendering. Solo per uso avanzato.                                                                                                                                                                                                                                                                  |                                                                                                                                            |

![Modalità di rendering](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| Modalità di abbattimento |             Descrizione                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Off       | Disabilita l'abbattimento della faccia. L'abbattimento deve essere impostato su off solo quando è necessaria una mesh bidirezionale.                                                                                        |
| Front     | Abilita l'abbattimento della faccia anteriore.                                                                                                                                                        |
| Indietro      | Predefinita Consente l' [abbattimento della faccia indietro](https://en.wikipedia.org/wiki/Back-face_culling). Per migliorare le prestazioni di rendering, è necessario abilitare l'abbattimento di back-face il più spesso possibile. |

## <a name="performance"></a>Prestazioni

Uno dei principali vantaggi dell'uso di MRTK standard shader rispetto a Unity standard shader è costituito dalle prestazioni. Lo shader standard MRTK è estendibile in modo da usare solo le funzionalità abilitate. Tuttavia, lo shader standard MRTK è stato scritto anche per offrire risultati estetici paragonabili come shader standard Unity, ma a un costo molto più basso. Un modo semplice per confrontare le prestazioni dello shader è tramite il numero di operazioni che è necessario eseguire sulla GPU. Naturalmente, la grandezza dei calcoli può variare in base alle funzionalità abilitate e ad altre configurazioni di rendering. Tuttavia, in generale, lo shader standard MRTK esegue un calcolo significativamente inferiore rispetto allo shader standard di Unity.

Esempio di statistiche shader standard Unity

![Statistiche dello shader standard Unity](../images/performance/UnityStandardShader-Stats.PNG)

Esempio di statistiche shader standard MRTK

![Statistiche dello shader standard MRTK](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> Questi risultati possono essere generati selezionando e visualizzando un [asset dello shader](https://docs.unity3d.com/Manual/class-Shader.html) nel controllo di Unity, quindi facendo clic sul pulsante *Compila e Mostra codice* .

## <a name="lighting"></a>Luce

MRTK/standard usa una semplice approssimazione per l'illuminazione. Poiché questo shader non calcola la correttezza fisica e la conservazione dell'energia, il rendering viene eseguito in modo rapido ed efficiente. Blinn-Phong è la tecnica di illuminazione principale, che viene mescolata con Fresnel e l'illuminazione basata su immagini per approssimare l'illuminazione fisica. Lo shader supporta le tecniche di illuminazione seguenti:

### <a name="directional-light"></a>Luce direzionale

Lo shader rispetta la direzione, il colore e l'intensità della prima luce direzionale di Unity nella scena (se abilitata). I punti luminosi dinamici, le luci spot o qualsiasi altra luce di Unity non verranno presi in considerazione nell'illuminazione in tempo reale.

### <a name="spherical-harmonics"></a>Armoniche sferiche

Lo shader userà sonde leggere per approssimare luci nella scena usando [armoniche sferiche](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html), se abilitate. I calcoli delle armoniche sferiche vengono eseguiti per ogni vertice per ridurre i costi di calcolo.

### <a name="lightmapping"></a>Lightmapping

Per l'illuminazione statica, lo shader rispetterà lightmaps compilata dal [sistema Lightmapping](https://docs.unity3d.com/Manual/Lightmapping.html)di Unity. È sufficiente contrassegnare il renderer come statico (o lightmap statico) per l'uso di lightmaps.

### <a name="hover-light"></a>Luce al passaggio del mouse

* Vedere la [luce del passaggio del mouse](hover-light.md)

### <a name="proximity-light"></a>Luce vicina

* Vedere la [luce vicina](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>Supporto semplificato per la pipeline di rendering con script

Il MRTK contiene un percorso di aggiornamento che consente agli sviluppatori di usare la pipeline di rendering con script Lightweight di Unity (LWRP) con MRTK shader. Testato in Unity 2019.1.1 F1 e Lightweight RP 5.7.2 Package. per istruzioni su come iniziare a usare LWRP, vedere [Questa pagina](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html).

Per eseguire l'aggiornamento di MRTK, selezionare il **Toolkit di realtà mista-> Utilities-> aggiornare lo shader standard MRTK per la pipeline di rendering semplice**

![aggiornamento di lwrp](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

Una volta eseguito l'aggiornamento, lo shader MRTK/standard verrà modificato ed eventuali materiali Magenta (errore shader) dovranno essere corretti. Per verificare che l'aggiornamento sia stato eseguito correttamente, controllare la console di: **aggiornato assets/MixedRealityToolkit/StandardAssets/shaders/MixedRealityStandard. shader per l'uso con la pipeline di rendering Lightweight.**

## <a name="ugui-support"></a>Supporto di UGUI

Il sistema di ombreggiatura standard MRTK funziona con il sistema di [interfaccia utente](https://docs.unity3d.com/Manual/UISystem.html)incorporato di Unity. Nei componenti dell'interfaccia utente di Unity, la matrice di unity_ObjectToWorld non è la matrice di trasformazione della trasformazione locale su cui si trova il componente grafico, ma quella dell'area di disegno padre. Molti effetti dello shader MRTK/standard richiedono che la scala degli oggetti sia nota. Per risolvere questo problema, [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) archivia le informazioni di ridimensionamento negli attributi del canale UV durante la costruzione della mesh dell'interfaccia utente.

Si noti che quando si usa un componente immagine Unity, è consigliabile specificare "None (sprite)" per l'immagine di origine per impedire che l'interfaccia utente di Unity crei vertici aggiuntivi.

Un'area di disegno all'interno del MRTK richiederà l'aggiunta di un [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) quando necessario:

![Ridimensiona effetto mesh](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>Combinatore trama

Per migliorare la parità con lo shader standard Unity per pixel, i valori metallic, smoothity, emissivo e occlusion possono essere controllati tramite la [compressione del canale](http://wiki.polycount.com/wiki/ChannelPacking). Ad esempio:

![esempio di mappa del canale](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

Quando si usa la compressione del canale, è necessario campionare e caricare una sola trama in memoria invece di quattro separate. Quando si scrivono le mappe di trama in un programma come sostanza o Photoshop, è possibile passare a un pacchetto simile al seguente:

| Canale | Proprietà             |
|---------|----------------------|
| Red     | Metallica             |
| Green   | Occlusione            |
| Blu    | Emissione (scala di grigi) |
| Alfa   | Scorrevolezza           |

In alternativa, è possibile usare lo strumento MRTK texture Combiner. Per aprire lo strumento, selezionare: **mixed reality Toolkit-> Utilities-> texture Combiner** che consente di aprire la finestra seguente:

![esempio di combinazione di trame](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Questa finestra può essere compilata automaticamente selezionando uno shader standard Unity e facendo clic su "popolamento automatico da materiale standard". In alternativa, è possibile specificare manualmente una trama (o un valore costante) per canale rosso, verde, blu o alfa. La combinazione di trame è accelerata con GPU e non richiede che la trama di input sia accessibile alla CPU.

## <a name="additional-feature-documentation"></a>Documentazione aggiuntiva sulle funzionalità

Di seguito sono riportate informazioni aggiuntive su alcuni dettagli delle funzionalità disponibili con lo shader MRTK/standard.

### <a name="primitive-clipping"></a>Ritaglio primitivo

![ritaglio primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* Vedere [primitiva di ritaglio](clipping-primitive.md)

### <a name="mesh-outlines"></a>Strutture mesh

Molte tecniche di struttura mesh vengono eseguite utilizzando una tecnica di [post-elaborazione](https://docs.unity3d.com/Manual/PostProcessingOverview.html) . La post-elaborazione fornisce strutture di qualità elevata, ma può essere eccessivamente costosa in molti dispositivi di realtà mista. È possibile trovare una scena che illustra l'uso di strutture mesh nella scena  **OutlineExamples** sotto `MRTK/Examples/Demos/StandardShader/Scenes/` .

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) e [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) possono essere usati per eseguire il rendering di una struttura intorno a un renderer mesh. L'abilitazione di questo componente introduce un passaggio di rendering aggiuntivo dell'oggetto che viene descritto, ma è progettato per eseguire performantly nei dispositivi mobili di realtà mista e non usa alcun processo post. Le limitazioni di questo effetto includono che non funziona bene per gli oggetti che non sono stagni (o che devono essere bilaterali) ed è possibile che si verifichino problemi di ordinamento di profondità sugli oggetti sovrapposti.

I comportamenti del contorno sono progettati per essere usati insieme allo shader MRTK/standard. I materiali di contorno sono in genere un colore spento, ma possono essere configurati per ottenere una vasta gamma di effetti. La configurazione predefinita di un materiale della struttura è la seguente:

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. Depth Write: deve essere disabilitato per i materiali della struttura per assicurarsi che la struttura non impedisca il rendering di altri oggetti.
2. Estrusione dei vertici: è necessario abilitare per eseguire il rendering della struttura.
3. USA smooth normals: questa impostazione è facoltativa per alcune mesh. L'estrusione viene eseguita spostando un vertice lungo una normale del vertice, in alcune mesh l'estrusione lungo le normali predefinite provocherà discontinuità nel contorno. Per correggere queste discontinuità, è possibile selezionare questa casella per usare un altro set di normali uniformi che vengono generati da [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) è un componente che può essere utilizzato per generare automaticamente normali uniformi su una mesh. Questo metodo raggruppa i vertici in una mesh che condividono la stessa posizione nello spazio, quindi calcola la media dei normali vertici. Questo processo crea una copia della mesh sottostante e deve essere usata solo quando richiesto.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. Normali normali generate tramite [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) .
2. Valori normali predefiniti usati. si notino gli elementi intorno agli angoli del cubo.

### <a name="stencil-testing"></a>Test di stencil

Incorporato supporto per test di stencil configurabili per ottenere una vasta gamma di effetti. Ad esempio i portali:

![test stencil](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>Supporto di colori per istanza

Supporto dei colori dell'istanza per concedere a migliaia di mesh di istanze GPU le proprietà del materiale univoche:

![Proprietà istanza](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Mapping Triplanare

Il mapping Tripiano è una tecnica per la trama a livello di codice di una mesh. Spesso usato in un terreno, mesh senza UV o con difficoltà nell'annullare il wrapping di forme. Questa implementazione supporta la proiezione dello spazio globale o locale, la specifica della uniformità della sfumatura e il normale supporto della mappa. Si noti che per ogni trama utilizzata sono necessari 3 esempi di trama, pertanto è necessario utilizzare le situazioni critiche per le prestazioni.

![Triplanare](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>Estrusione di vertici

Estrusione di vertici nello spazio globale. Utile per visualizzare i volumi di delimitazione estrusi o le transizioni in/out mesh.

![scala normale mappa 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>Varie

Casella di controllo per controllare le ottimizzazioni di albedo. Poiché le operazioni di ottimizzazione Albedo vengono disabilitate quando non viene specificata alcuna trama di albedo. Questa operazione è utile per controllare il [caricamento di trame Remote](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html).

È sufficiente selezionare questa casella:

![assegnazione albedo](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

Sono supportate le trame di ritaglio per pixel, l'anti-aliasing basato su Edge locale e il ridimensionamento normale della mappa.

![scala mappa normale 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>Vedi anche

* [Con cui](../ux-building-blocks/interactable.md)
* [Luce al passaggio del mouse](hover-light.md)
* [Luce vicina](proximity-light.md)
* [Primitiva di ritaglio](clipping-primitive.md)
