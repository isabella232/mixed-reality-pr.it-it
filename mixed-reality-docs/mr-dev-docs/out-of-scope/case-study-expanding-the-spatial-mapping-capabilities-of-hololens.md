---
title: Case study - Espansione delle funzionalità di mapping spaziale di HoloLens
description: Quando si creano le prime app per Microsoft HoloLens, è stato utile vedere fino a che punto è stato possibile eseguire il push dei limiti del mapping spaziale nel dispositivo.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, mapping spaziale
ms.openlocfilehash: f0438990c39570f9188e2e150a8cbe7907d72f7e2be260c72e41646565b8d89e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210447"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Case study - Espansione delle funzionalità di mapping spaziale di HoloLens

Quando si creano le prime app per Microsoft HoloLens, è stato utile vedere fino a che punto è stato possibile eseguire il push dei limiti del mapping spaziale nel dispositivo. Jeff Evertt, software engineer di Microsoft Studio, spiega come è stata sviluppata una nuova tecnologia per la necessità di un maggiore controllo sul modo in cui gli ologrammi vengono inseriti nell'ambiente reale di un utente.

> [!NOTE]
> HoloLens 2 implementa un nuovo runtime [scene understanding,](../design/scene-understanding.md)che offre agli sviluppatori di realtà mista una rappresentazione strutturata e di alto livello dell'ambiente progettata per rendere intuitivo lo sviluppo per applicazioni in grado di riconoscere l'ambiente. 

## <a name="watch-the-video"></a>Video

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Oltre il mapping spaziale

Mentre si lavora a [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) e [Young Conker,](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)due dei primi giochi per HoloLens, si è scoperto che quando si stava eseguendo il posizionamento procedurale degli ologrammi nel mondo fisico, era necessario un livello più elevato di comprensione dell'ambiente dell'utente. Ogni gioco aveva esigenze specifiche di posizionamento: in Frammenti, ad esempio, si voleva essere in grado di distinguere tra superfici diverse, ad esempio il piano o un tavolo, per inserire indizi nelle posizioni pertinenti. Si voleva anche poter identificare le superfici su cui potevano sedersi i caratteri olografici a dimensione reale, ad esempio un divano o un letto. In Young Conker si voleva che Conker e i suoi figli possano usare le superfici in rilievo nella stanza di un giocatore come piattaforme.

[Asobo Studio,](https://www.asobostudio.com/index.html)il partner di sviluppo per questi giochi, ha affrontato questo problema e ha creato una tecnologia che estende le funzionalità di mapping spaziale di HoloLens. In questo modo, è possibile analizzare la stanza di un giocatore e identificare superfici come pareti, tabelle, pareti e piani. Ha inoltre offerto la possibilità di eseguire l'ottimizzazione in base a un set di vincoli per determinare la posizione migliore per gli oggetti olografici.

## <a name="the-spatial-understanding-code"></a>Codice di comprensione spaziale

È stato preso il codice originale di Asobo ed è stata creata una libreria che incapsula questa tecnologia. Microsoft e Asobo hanno ora reso open source questo codice e lo hanno reso disponibile in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) per l'uso nei propri progetti. Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle proprie esigenze e condividere i miglioramenti con la community. Il codice per il risolutore C++ è stato incapsulato in una DLL UWP ed esposto a Unity con un prefab di rilascio contenuto in [MixedRealityToolkit.](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)

Nell'esempio unity sono incluse molte query utili che consentono di trovare spazi vuoti sulle pareti, posizionare oggetti sul controsoffitto o su spazi di grandi dimensioni sul piano, identificare i luoghi in cui si trovano i caratteri e una miriade di altre query di comprensione spaziale.

Anche se la soluzione di mapping spaziale fornita da HoloLens è progettata per essere sufficientemente generica da soddisfare le esigenze dell'intera gamma di spazi problematici, il modulo di comprensione spaziale è stato creato per supportare le esigenze di due giochi specifici. Di conseguenza, la soluzione è strutturata in base a un processo specifico e a un set di presupposti:
* **Spazio di riproduzione a dimensione** fissa: l'utente specifica le dimensioni massime dello spazio di riproduzione nella chiamata init.
* **Processo di analisi una sola volta:** il processo richiede una fase di analisi discreta in cui l'utente si aggira, definendo lo spazio di riproduzione. Le funzioni di query funzioneranno solo dopo la finalizzazione dell'analisi.
* **"disegno" dello spazio** di gioco guidato dall'utente: durante la fase di analisi, l'utente si sposta e guarda intorno al playspace, disegnando in modo efficace le aree che devono essere incluse. La mesh generata è importante per fornire commenti e suggerimenti durante questa fase.
* **Configurazione dell'ambiente domestico o** dell'ufficio: le funzioni di query sono progettate su superfici piatte e pareti ad angolo retto. Si tratta di una limitazione soft. Durante la fase di analisi, tuttavia, viene completata un'analisi dell'asse principale per ottimizzare la trama mesh lungo l'asse principale e secondario.

### <a name="room-scanning-process"></a>Processo di analisi delle camere

Quando si carica il modulo di comprensione spaziale, la prima cosa da fare è analizzare lo spazio, in modo che tutte le superfici utilizzabili, ad esempio il piano, il controsoffitto e le pareti, siano identificate ed etichettate. Durante il processo di scansione, si guarda intorno alla stanza e si "disegnano" le aree che devono essere incluse nell'analisi.

La mesh vista durante questa fase è un elemento importante del feedback visivo che consente agli utenti di sapere quali parti della stanza vengono analizzate. La DLL per il modulo spatial understanding archivia internamente lo spazio di riproduzione come griglia di cubi voxel con dimensioni di 8 cm. Durante la parte iniziale dell'analisi, viene completata un'analisi dei componenti principali per determinare gli assi della stanza. Internamente, archivia lo spazio voxel allineato a questi assi. Una mesh viene generata circa ogni secondo estraendo l'isosurface dal volume voxel.

![Mesh di mapping spaziale in bianco e mesh di playspace in verde](images/spatial-mapping-500px.png)

Mesh di mapping spaziale in bianco e mesh di playspace in verde



Il file SpatialUnderstanding.cs incluso gestisce il processo della fase di analisi. Chiama le funzioni seguenti:
* **SpatialUnderstanding_Init**: chiamato una volta all'inizio.
* **GeneratePlayspace_InitScan**: indica che deve iniziare la fase di analisi.
* **GeneratePlayspace_UpdateScan_DynamicScan**: chiamato ogni frame per aggiornare il processo di analisi. La posizione e l'orientamento della fotocamera vengono passati e usati per il processo di disegno dello spazio di riproduzione, descritto in precedenza.
* **GeneratePlayspace_RequestFinish**: chiamato per finalizzare lo spazio di riproduzione. Verranno usate le aree "disegnate" durante la fase di analisi per definire e bloccare lo spazio di riproduzione. L'applicazione può eseguire query sulle statistiche durante la fase di analisi, nonché eseguire query sulla mesh personalizzata per fornire commenti e suggerimenti degli utenti.
* **Import_UnderstandingMesh:** durante l'analisi, il comportamento **SpatialUnderstandingCustomMesh** fornito dal modulo e inserito nel prefab di comprensione esegue periodicamente una query sulla mesh personalizzata generata dal processo. Inoltre, questa operazione viene eseguita ancora una volta dopo la finalizzazione dell'analisi.

Il flusso di analisi, basato sul comportamento **SpatialUnderstanding,** chiama **InitScan** e **quindi UpdateScan per** ogni fotogramma. Quando la query sulle statistiche segnala una copertura ragionevole, l'utente può effettuare il airtap per chiamare **RequestFinish** per indicare la fine della fase di analisi. **UpdateScan** continua a essere chiamato fino a quando il valore restituito non indica che l'elaborazione della DLL è stata completata.

## <a name="the-queries"></a>Query

Al termine dell'analisi, sarà possibile accedere a tre diversi tipi di query nell'interfaccia:
* **Query di topologia:** si tratta di query veloci basate sulla topologia della stanza analizzata.
* **Query di** forma: utilizzano i risultati delle query sulla topologia per trovare superfici orizzontali che sono una buona corrispondenza con le forme personalizzate definite dall'utente.
* **Query di posizionamento** degli oggetti: query più complesse che trovano la posizione più adatta in base a un set di regole e vincoli per l'oggetto.

Oltre alle tre query principali, è disponibile un'interfaccia di raycasting che può essere usata per recuperare i tipi di superficie con tag ed è possibile copiare una mesh di stanza stagna personalizzata.

### <a name="topology-queries"></a>Query sulla topologia

All'interno della DLL, il gestore della topologia gestisce l'etichettatura dell'ambiente. Come accennato in precedenza, gran parte dei dati viene archiviata all'interno di un volume voxel. Inoltre, la struttura **PlaySpaceInfos** viene usata per archiviare le informazioni sullo spazio di gioco, tra cui l'allineamento del mondo (altri dettagli su questo di seguito), il piano e l'altezza del controsoffitto.

L'euristica viene usata per determinare il piano, il controsoffitto e le pareti. Ad esempio, la superficie orizzontale più grande e più bassa con una superficie di superficie maggiore di 1 m2 viene considerata il piano. Si noti che in questo processo viene usato anche il percorso della fotocamera durante il processo di analisi.

Un subset delle query esposte dal gestore della topologia viene esposto tramite la DLL. Le query sulla topologia esposte sono le seguenti:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Ognuna delle query ha un set di parametri, specifico per il tipo di query. Nell'esempio seguente l'utente specifica l'altezza minima & larghezza del volume desiderato, l'altezza di posizionamento minima sopra il piano e la quantità minima di spazio davanti al volume. Tutte le misurazioni sono in metri.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Ognuna di queste query accetta una matrice preallocato **di strutture TopologyResult.** Il **parametro locationCount** specifica la lunghezza della matrice passata. Il valore restituito indica il numero di posizioni restituite. Questo numero non è mai maggiore del parametro **locationCount** passato.

**TopologyResult contiene** la posizione centrale del volume restituito, la direzione rivolta verso (normale) e le dimensioni dello spazio trovato.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Si noti che nell'esempio di Unity ognuna di queste query è collegata a un pulsante nel pannello dell'interfaccia utente virtuale. L'esempio imposta come hard code i parametri per ognuna di queste query in base a valori ragionevoli. Per *altri esempi, vedere SpaceVisualizer.cs* nel codice di esempio.

### <a name="shape-queries"></a>Modellare le query

All'interno della DLL, l'analizzatore forme (**ShapeAnalyzer_W**) usa l'analizzatore della topologia per la corrispondenza con forme personalizzate definite dall'utente. L'esempio Unity ha un set predefinito di forme che vengono visualizzate nel menu della query, nella scheda della forma.

Si noti che l'analisi delle forme funziona solo su superfici orizzontali. Un divano, ad esempio, è definito dalla superficie della sella piana e dalla parte superiore piana del divano. La query di forma cerca due superfici di dimensioni, altezza e intervallo di aspetti specifici, con le due superfici allineate e connesse. Usando la terminologia delle API, il posto sul divano e la parte superiore del divano sono componenti di forma e i requisiti di allineamento sono vincoli dei componenti della forma.

Una query di esempio definita nell'esempio unity (**ShapeDefinition.cs**) per gli oggetti "sittable" è la seguente:




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

Ogni query di forma è definita da un set di componenti della forma, ognuno con un set di vincoli di componente e un set di vincoli di forma che elenca le dipendenze tra i componenti. Questo esempio include tre vincoli in una singola definizione di componente e nessun vincolo di forma tra i componenti (poiché è presente un solo componente).

Al contrario, la forma del divano ha due componenti di forma e quattro vincoli di forma. Si noti che i componenti sono identificati dal relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Le funzioni wrapper vengono fornite nel modulo Unity per creare facilmente definizioni di forme personalizzate. L'elenco completo dei vincoli di componente e forma è disponibile in **SpatialUnderstandingDll.cs** all'interno delle strutture **ShapeComponentConstraint** e **ShapeConstraint.**

![Il rettangolo blu evidenzia i risultati della query di forma della forma di forma.](images/chair-shape-query-500px.png)

Il rettangolo blu evidenzia i risultati della query di forma della forma di forma.



### <a name="object-placement-solver"></a>Risolutore di posizionamento degli oggetti

Le query di posizionamento degli oggetti possono essere usate per identificare le posizioni ideali nella stanza fisica in cui posizionare gli oggetti. Il risolutore troverà la posizione più adatta in base alle regole e ai vincoli dell'oggetto. Inoltre, le query su oggetti vengono mantenute fino a quando l'oggetto non viene rimosso **con** Solver_RemoveObject o **Solver_RemoveAllObjects,** consentendo il posizionamento vincolato di più oggetti.

Le query di posizionamento degli oggetti sono costituite da tre parti: il tipo di posizionamento con parametri, un elenco di regole e un elenco di vincoli. Per eseguire una query, usare l'API seguente:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
Questa funzione accetta un nome di oggetto, una definizione di posizionamento e un elenco di regole e vincoli. I wrapper C# forniscono funzioni helper di costruzione per semplificare la costruzione di regole e vincoli. La definizione di posizionamento contiene il tipo di query , ovvero uno dei seguenti:




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

Ogni tipo di posizionamento ha un set di parametri univoci per il tipo. La **struttura ObjectPlacementDefinition** contiene un set di funzioni helper statiche per la creazione di queste definizioni. Ad esempio, per trovare una posizione in cui inserire un oggetto sul piano, è possibile usare la funzione seguente: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Oltre al tipo di posizionamento, è possibile fornire un set di regole e vincoli. Le regole non possono essere violate. Le possibili posizioni di posizionamento che soddisfano il tipo e le regole vengono quindi ottimizzate rispetto al set di vincoli per selezionare la posizione ottimale. Ogni regola e vincolo può essere creato dalle funzioni di creazione statiche fornite. Di seguito è riportata una regola di esempio e una funzione di costruzione di vincoli.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La query di posizionamento degli oggetti riportata di seguito cerca un punto in cui posizionare un cubo di mezzo metro sul bordo di una superficie, lontano da altri oggetti posizionati in precedenza e vicino al centro della stanza.




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

In caso di esito positivo, viene restituita una struttura **ObjectPlacementResult** contenente la posizione di posizionamento, le dimensioni e l'orientamento. Inoltre, il posizionamento viene aggiunto all'elenco interno della DLL di oggetti inseriti. Le query di posizionamento successive prenderanno in considerazione questo oggetto. Il file **LevelSolver.cs** nell'esempio Unity contiene altre query di esempio.

![Le caselle blu mostrano il risultato di tre query Place On Floor con regole "lontano dalla posizione della fotocamera".](images/away-from-camera-position-500px.png)

Le caselle blu mostrano il risultato di tre query Place On Floor con regole "lontano dalla posizione della fotocamera".


**Suggerimenti:**
* Durante la risoluzione della posizione di posizionamento di più oggetti necessari per uno scenario di livello o applicazione, risolvere prima di tutto oggetti di grandi dimensioni e di grandi dimensioni per ottimizzare la probabilità che sia possibile trovare uno spazio.
* L'ordine di posizionamento è importante. Se non è possibile trovare i posizionamenti degli oggetti, provare le configurazioni meno vincolate. La presenza di un set di configurazioni di fallback è fondamentale per supportare le funzionalità in molte configurazioni di stanza.

### <a name="ray-casting"></a>Ray casting

Oltre alle tre query principali, è possibile usare un'interfaccia di ray casting per recuperare i tipi di superficie con tag e copiare una mesh dello spazio di gioco personalizzata dopo che la stanza è stata analizzata e finalizzata, le etichette vengono generate internamente per superfici come il piano, il controsoffitto e le pareti. La **funzione PlayspaceRaycast** accetta un raggio e restituisce se il raggio entra in conflitto con una superficie nota e, in tal caso, le informazioni su tale superficie sotto forma di **RaycastResult.** 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

Internamente, il raycast viene calcolato in base alla rappresentazione del voxel cubi di 8 cm calcolata dello spazio di riproduzione. Ogni voxel contiene un set di elementi di superficie con dati di topologia elaborati (noti anche come surfel). Vengono confrontate le superfici contenute all'interno della cella voxel intersecata e viene usata la corrispondenza migliore per cercare le informazioni sulla topologia. Questi dati della topologia contengono l'etichettatura restituita sotto forma di **enumerazione SurfaceTypes,** nonché la superficie della superficie intersecata.

Nell'esempio unity il cursore esegue il cast di un raggio per ogni frame. In primo luogo, contro i collisori di Unity; secondo, rispetto alla rappresentazione del mondo del modulo di comprensione; e infine rispetto agli elementi dell'interfaccia utente. In questa applicazione, l'interfaccia utente ottiene la priorità, quindi il risultato di comprensione e infine i collisori di Unity. SurfaceType **viene** segnalato come testo accanto al cursore.

![Raycast result reporting intersection with the floor.](images/raycast-result-500px.jpg)

Raycast result reporting intersection with the floor.


## <a name="get-the-code"></a>Ottenere il codice

Il codice open source è disponibile in [MixedRealityToolkit.](https://github.com/Microsoft/MixedRealityToolkit-Unity) Se si usa il [codice in un progetto, HoloLens forum](https://forums.hololens.com/) per sviluppatori di Microsoft. Non vediamo l'ora di vedere cosa si fa con esso.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> è un software engineering lead che ha lavorato a HoloLens fin dai primi tempi, dall'incubazione all'esperienza di sviluppo. Prima HoloLens, ha lavorato a Xbox Kinect e nel settore dei giochi su un'ampia gamma di piattaforme e giochi. Jeff è appassionato di robotica, grafica e cose con luci lampeggianti che esercitino. Si diverte a imparare nuove cose e a lavorare su software, hardware e in particolare nello spazio in cui si intersecano i due.</td>
</tr>
</table>



## <a name="see-also"></a>Vedere anche
* [Mapping spaziale](../design/spatial-mapping.md)
* [Informazioni sulle scene](../design/scene-understanding.md)
* [Visualizzazione della scansione dello spazio](../design/room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: lezioni di prima linea per lo HoloLens sviluppo](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
