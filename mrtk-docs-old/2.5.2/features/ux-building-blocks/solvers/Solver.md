---
title: Solver
description: Panoramica dei risolutori in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, risolutori,
ms.openlocfilehash: affc62145fa46939cf12c71f0233df28f93e07dc
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782523"
---
# <a name="solvers"></a>Risolutori

![Principale Risolutore](../../images/solver/MRTK_Solver_Main.png)

I resolver sono componenti che facilitano il calcolo della posizione di un oggetto & orientamento in base a un algoritmo di predefinizione. Un esempio potrebbe essere l'inserimento di un oggetto sulla superficie a cui si riferisce lo sguardo Raycast dell'utente.  

Inoltre, il sistema di Risolutore definisce in modo deterministico un ordine di operazioni per questi calcoli di trasformazione, perché non esiste un modo affidabile per specificare l'ordine di aggiornamento per i componenti in Unity.

I risolutori offrono una gamma di comportamenti per aggiungere oggetti ad altri oggetti o sistemi. Un altro esempio è un oggetto con tag che passa davanti all'utente (in base alla fotocamera). Un Risolutore può anche essere collegato a un controller e a un oggetto per rendere il tag oggetto lungo il controller. Tutti i risolutori possono essere impilati in modo sicuro, ad esempio un comportamento di tag lungo e un magnetismo di superficie + momento.

## <a name="how-to-use-a-solver"></a>Come usare un risolutore

Il sistema del Risolutore è costituito da tre categorie di script:

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver): Classe astratta di base da cui derivano tutti i resolver. Fornisce il rilevamento dello stato, l'implementazione e i parametri di smoothing, l'integrazione automatica del sistema di risoluzione e l'ordine di aggiornamento.
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler): Imposta l'oggetto di riferimento da rilevare (ad esempio, la trasformazione della fotocamera principale, il raggio della mano e così via), gestisce la raccolta dei componenti del Risolutore ed esegue l'aggiornamento nell'ordine corretto.

La terza categoria è il Risolutore. I risolutori seguenti forniscono i blocchi predefiniti per il comportamento di base:

* [`Orbital`](#orbital): Blocca a una posizione e un offset specificati dall'oggetto a cui si fa riferimento.
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize): Scala per mantenere una dimensione costante rispetto alla visualizzazione dell'oggetto a cui si fa riferimento.
* [`RadialView`](#radialview): Mantiene l'oggetto all'interno di un cono di visualizzazione sottomesso a cast dall'oggetto a cui si fa riferimento.
* [`SurfaceMagnetism`](#surfacemagnetism): esegue il cast dei raggi alle superfici del mondo e allinea l'oggetto alla superficie.
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum): Applica accelerazione/velocità/attrito per simulare Momentum e Springiness per un oggetto spostato da altri resolver/componenti.
* [`InBetween`](#inbetween): Mantiene un oggetto tra due oggetti rilevati.
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup): Vincola l'oggetto a seguire le mani in un'area che non interseca GameObject con le mani. Utile per contenuto interattivo vincolato a mano, ad esempio menu e così via. Il Risolutore è progettato per funzionare con [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) , ma funziona anche con [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController).
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup): Deriva da HandConstraint, ma include la logica per verificare se il Palm è rivolte all'utente prima dell'attivazione. Il Risolutore funziona solo con i controller [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) , con altri tipi di controller che il Risolutore si comporterà esattamente come la classe di base.

Per usare il sistema di Risolutore, è sufficiente aggiungere uno dei componenti elencati in precedenza a un GameObject. Poiché tutti i risolutori richiedono un [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) , ne verrà creato uno automaticamente da Unity.

> [!NOTE]
> Esempi di come usare il sistema di risoluzione sono reperibili nel file **SolverExamples. scene** .

## <a name="how-to-change-tracking-reference"></a>Come modificare il riferimento al rilevamento

La proprietà del *tipo di destinazione rilevata* del [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) componente definisce il punto di riferimento che tutti i resolver utilizzeranno per calcolare i relativi algoritmi. Ad esempio, un tipo di valore [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) con un [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) componente semplice genererà un Raycast dalla parte iniziale e nella direzione dello sguardo dell'utente per la risoluzione della superficie da raggiungere. I valori potenziali per la `TrackedTargetType` proprietà sono:

* *Head* : il punto di riferimento è la trasformazione della fotocamera principale
* *ControllerRay*: il punto di riferimento è la [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) trasformazione in un controller (ad esempio origine puntatore in un controller di movimento o in un controller di mano) che punta alla direzione del raggio di linea
  * Utilizzare la `TrackedHandedness` proprietà per selezionare la preferenza di manualità (ad esempio Left, right, both)
* *HandJoint*: il punto di riferimento è la trasformazione di una giunzione a mano specifica
  * Utilizzare la `TrackedHandedness` proprietà per selezionare la preferenza di manualità (ad esempio Left, right, both)
  * Utilizzare la  `TrackedHandJoint` proprietà per determinare la trasformazione congiunta da utilizzare
* *CustomOverride*: punto di riferimento dall'oggetto assegnato `TransformOverride`

> [!NOTE]
> Per i tipi *ControllerRay* e *HandJoint* , il gestore del Risolutore tenterà di fornire prima la trasformazione a sinistra del controller o della mano, quindi il diritto se il primo non è disponibile o a meno che la `TrackedHandedness` proprietà non specifichi diversamente.

![Oggetto rilevato di esempio del Risolutore](../../images/solver/TrackedObjectType-Example.gif)  
*Esempio di varie proprietà associate a ogni TrackedTargetType*

> [!IMPORTANT]
> La maggior parte dei resolver usa il vettore di avanzamento della destinazione della trasformazione rilevata fornita da `SolverHandler` . Quando si usa un tipo di destinazione rilevata *congiuntamente* , il vettore di avanzamento del giunto della palma può puntare attraverso le dita e non attraverso il Palm. Questo dipende dalla piattaforma che fornisce i dati di giunzione. Per la simulazione di input e la realtà mista di Windows, è il *vettore up* che punta attraverso la Palma (ovvero il vettore verde è attivo, il vettore blu è in futuro.
>
> ![Vettori di avanzamento del Risolutore](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> Per ovviare a questo problema, aggiornare la proprietà *Rotation aggiuntiva* nel `SolverHandler` **<90, 0,0>**. In questo modo, il vettore di avanzamento fornito ai risolutori sta puntando attraverso la Palma e allontanandosi dall'esterno.
>
> ![Rotazione aggiuntiva del Risolutore](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> In alternativa, usare il tipo di destinazione del *raggio controller* rilevato per ottenere un comportamento simile per puntare con le mani.

## <a name="how-to-chain-solvers"></a>Come concatenare i risolutori

È possibile aggiungere più `Solver` componenti allo stesso GameObject concatenando quindi gli algoritmi. I `SolverHandler` componenti gestiscono l'aggiornamento di tutti i risolutori nello stesso GameObject. Per impostazione predefinita, le `SolverHandler` chiamate all' `GetComponents<Solver>()` avvio restituiscono i resolver nell'ordine in cui sono visualizzate nel controllo.

Inoltre, impostando la proprietà di *trasformazione collegata aggiornata* su true, viene indicato che `Solver` per salvare la posizione calcolata, l'orientamento & la scalabilità in una variabile intermedia accessibile da tutti i risolutori (ad esempio `GoalPosition`). Se false, `Solver` aggiornerà direttamente la trasformazione del GameObject. Salvando le proprietà di trasformazione in un percorso intermedio, altri risolutori sono in grado di eseguire i calcoli a partire dalla variabile intermedia. In quanto Unity non consente l'aggiornamento di gameObject. Transform nello stack nello stesso frame.

> [!NOTE]
> Gli sviluppatori possono modificare l'ordine di esecuzione dei risolutori impostando `SolverHandler.Solvers` direttamente la proprietà.

## <a name="how-to-create-a-new-solver"></a>Come creare un nuovo Risolutore

Tutti i risolutori devono ereditare dalla classe di base astratta [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver) . I requisiti principali di un'estensione del Risolutore implica l'override del `SolverUpdate` metodo. In questo metodo, gli sviluppatori devono aggiornare le `GoalPosition` proprietà ereditate `GoalRotation` e `GoalScale` ai valori desiderati. Inoltre, in genere è utile utilizzare `SolverHandler.TransformTarget` come frame di riferimento desiderato dal consumer.

Il codice riportato di seguito fornisce un esempio di un nuovo componente del Risolutore denominato `InFront` che inserisce l'oggetto collegato 2m davanti a `SolverHandler.TransformTarget` . Se l'oggetto `SolverHandler.TrackedTargetType` è impostato dal consumer come [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) , `SolverHandler.TransformTarget` sarà la trasformazione della fotocamera e pertanto il Risolutore inserirà il GameObject di allegato 2m davanti allo sguardo di tutti i frame degli utenti.

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>Guide all'implementazione del Risolutore

### <a name="common-solver-properties"></a>Proprietà del Risolutore comune

Ogni componente del Risolutore dispone di un set di base di proprietà identiche che controllano il comportamento del Risolutore principale.

Se la *smussatura* è abilitata, il Risolutore aggiornerà gradualmente la trasformazione del GameObject nel tempo ai valori calcolati. La velocità di questa modifica è determinata dalla proprietà *LerpTime* di ogni componente di trasformazione. Ad esempio, un valore *MoveLerpTime* più elevato provocherà incrementi più lenti nello spostamento tra i frame.

Se *MaintainScale* è abilitato, il Risolutore utilizzerà la scala locale predefinita di GameObject.

![Proprietà del Risolutore principale](../../images/solver/GeneralSolverProperties.png)  
*Proprietà comuni ereditate da tutti i componenti del Risolutore*

### <a name="orbital"></a>Orbitale

La [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) classe è un componente lungo tag che si comporta come i pianeti in un sistema solare. Il Risolutore assicurerà che il GameObject collegato orbiti attorno alla trasformazione rilevata. Pertanto, se il *tipo di destinazione rilevata* di [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) è impostato su [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) , il GameObject verrà orbitato intorno all'Head dell'utente con un offset fisso applicato.

Gli sviluppatori possono modificare questo offset fisso per tenere i menu o altri componenti della scena a livello di occhio o di vita e così via, intorno a un utente. Questa operazione viene eseguita modificando le proprietà *offset locale* e *offset globale* . La proprietà *tipo orientamento* determina la rotazione applicata all'oggetto se deve mantenere la rotazione originale o sempre rivolta alla fotocamera o alla superficie di qualsiasi trasformazione che sta determinando la posizione e così via.

![Esempio di orbita](../../images/solver/OrbitalExample.png)  
*Esempio di orbita*

### <a name="radialview"></a>RadialView

[`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView)È un altro componente di tag lungo che mantiene una parte specifica di un GameObject all'interno di tronco della visualizzazione dell'utente.

Le proprietà *Min & Max View degrees* determinano la quantità di una parte di GameObject che deve essere sempre visualizzata in visualizzazione.

Le proprietà *Min & max distance* determinano il modo in cui il GameObject deve essere mantenuto dall'utente. Ad esempio, se si cammina verso la GameObject con una *distanza minima* di 1m, il GameObject verrà spinto per assicurarsi che non sia mai più vicino a 1 milione di utenti.

In genere, [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) viene usato insieme al *tipo di destinazione rilevato* impostato su in [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) modo che il componente segua lo sguardo dell'utente. Tuttavia, questo componente può funzionare per essere mantenuto in *"View"* di qualsiasi *tipo di destinazione rilevato*.

![Esempio di RadialView](../../images/solver/RadialViewExample.png)  
*Esempio di RadialView*

### <a name="inbetween"></a>InBetween

La [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) classe manterrà il GameObject collegato tra due trasformazioni. Questi due endpoint di trasformazione sono definiti dal [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) *tipo di destinazione rilevata* di GameObject e dalla [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) seconda proprietà del *tipo di destinazione rilevata* del componente. In genere, entrambi i tipi verranno impostati su [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride) e i `SolverHandler.TransformOverride` valori e risultante `InBetween.SecondTransformOverride` impostati sui due endpoint rilevati.

In fase di esecuzione, il [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) componente creerà un altro [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) componente in base al *secondo tipo di destinazione rilevata* e alle *seconde* proprietà di sostituzione della trasformazione.

`PartwayOffset`Definisce la posizione lungo la linea tra due trasformazioni. l'oggetto deve essere inserito con 0,5 a metà, 1,0 alla prima trasformazione e 0,0 alla seconda trasformazione.

![Esempio di inbetween](../../images/solver/InBetweenExample.png)  
*Esempio di utilizzo di inbetween Solver per la conservazione di un oggetto tra due trasformazioni*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

Il [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) funziona eseguendo un Raycast su un set LayerMask di superfici e inserendo il GameObject in corrispondenza del punto di contatto.

L' *offset normale della superficie* GameObject la distanza del set in metri dalla superficie nella direzione della normale in corrispondenza del punto in cui si è verificata la superficie.

Viceversa, l'offset del *raggio della superficie* posiziona il GameObject in un set di distanza in metri di distanza dall'area, ma nella direzione opposta del Raycast eseguito. Quindi, se il Raycast è lo sguardo dell'utente, il GameObject verrà spostato più a lungo sulla linea dal punto di riscontro sulla superficie della fotocamera.

La *modalità di orientamento* determina il tipo di rotazione da applicare in relazione al normale sulla superficie.

* *None* : nessuna rotazione applicata
* *TrackedTarget* : l'oggetto affronterà la trasformazione tracciata che guida il Raycast
* *SurfaceNormal* -l'oggetto viene allineato in base al normale punto di hit sulla superficie
* *Blended* -Object viene allineato in base al normale punto di hit sulla superficie e in base alla trasformazione rilevata.

Per forzare il GameObject associato a rimanere verticale in qualsiasi modalità diversa da *nessuno*, abilitare *Mantieni orientamento verticale*.

> [!NOTE]
> Usare la proprietà *Orientation Blend* per controllare il saldo tra i fattori di rotazione quando la *modalità di orientamento* è impostata su *blended*. Il valore 0,0 avrà orientamento interamente guidato dalla modalità *TrackedTarget* e il valore 1,0 avrà orientamento interamente basato su *SurfaceNormal*.

![Esempio di SurfaceMagnetism](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>Determinazione delle superfici che è possibile raggiungere

Quando si aggiunge un [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) componente a un GameObject, è importante considerare il livello di GameObject e dei relativi elementi figlio, se presenti. Il componente funziona eseguendo vari tipi di raycasts per determinare la superficie a cui "magnete". Se il GameObject del Risolutore dispone di un Collider su uno dei livelli elencati nella `MagneticSurfaces` proprietà di `SurfaceMagnetism` , il Raycast probabilmente si raggiungerà a sua volta causando la connessione del GameObject al punto di Collider. Questo comportamento dispari può essere evitato impostando il GameObject principale e tutti gli elementi figlio sul livello *Ignora Raycast* o modificando in `MagneticSurfaces` modo appropriato la matrice LayerMask.

Viceversa, un [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) GameObject non entrerà in conflitto con le superfici su un livello non elencato nella `MagneticSurfaces` Proprietà. È in genere consigliabile posizionare tutte le superfici desiderate su un livello dedicato (ad esempio *Superfici*) e impostando la `MagneticSurfaces` proprietà solo su questo livello.  Per *impostazione predefinita* , è possibile che i componenti dell'interfaccia *utente o i* cursori contribuiscano al Risolutore.

Infine, le superfici più lontane dell' `MaxRaycastDistance` impostazione della proprietà verranno ignorate da `SurfaceMagnetism` raycasts.

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>Menu a mano con HandConstraint e HandConstraintPalmUp

![Esempio di UX menu a mano](../../images/solver/MRTK_UX_HandMenu.png)

Il [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) comportamento fornisce un risolutore che vincola l'oggetto rilevato a un'area sicura per il contenuto vincolato della mano, ad esempio l'interfaccia utente, i menu e così via. Le aree sicure sono considerate aree che non si intersecano con la mano. Viene inoltre inclusa una classe derivata di [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) chiamata [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) per illustrare un comportamento comune di attivazione dell'oggetto rilevato del Risolutore quando il Palm è rivolte all'utente.

Per esempi relativi all'uso del Risolutore di vincoli di mano, [vedere la pagina del menu](../HandMenu.md) a mano per creare menu a mano.

## <a name="experimental-solvers"></a>Risolutori sperimentali

Questi resolver sono disponibili in MRTK, ma sono attualmente sperimentali. Le API e le funzionalità sono soggette a modifiche. L'affidabilità e la qualità possono inoltre essere inferiori alle funzionalità standard.

### <a name="directional-indicator"></a>Indicatore direzionale

La [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Experimental.Utilities.DirectionalIndicator) classe è un componente lungo tag che si orienta alla direzione di un punto desiderato nello spazio.

Utilizzato più di frequente quando il *tipo di destinazione rilevato* di [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) è impostato su [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) . In questo modo, un componente UX con il [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Experimental.Utilities.DirectionalIndicator)  Risolutore consentirà all'utente di esaminare il punto desiderato nello spazio.

Il punto desiderato nello spazio viene determinato tramite la proprietà di *destinazione direzionale* .

Se la destinazione direzionale è visualizzabile dall'utente o qualsiasi frame di riferimento è impostato in, il [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) Risolutore Disabilita tutti i [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) componenti sottostanti. Se non visualizzabile, tutto verrà abilitato sull'indicatore.

* *Fattore di scala visibilità* -moltiplicatore per aumentare o diminuire il FOV che determina se il punto di *destinazione direzionale* è visualizzabile o meno
* *Offset visualizzazione* : dal punto di vista del frame di riferimento (ad esempio fotocamera possibilmente), questa proprietà definisce la distanza nella direzione dell'indicatore nell'oggetto dal centro del viewport.

![Proprietà indicatore direzionale](../../images/solver/DirectionalIndicatorExample.png)  
*Proprietà indicatore direzionale*

![Scena di esempio indicatore direzionale](../../images/solver/DirectionalIndicatorExampleScene.gif)

*Scenario di esempio dell'indicatore direzionale (assets/MRTK/examples/Experimental/solvers/DirectionalIndicatorExample. Unity)*

## <a name="see-also"></a>Vedi anche

* [Rilevamento della mano](../../input/HandTracking.md)
* [Sguardo fisso](../../input/Gaze.md)
