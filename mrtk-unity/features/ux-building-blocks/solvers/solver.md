---
title: Panoramica del risolutore
description: Panoramica dei risolutori in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, risolutori,
ms.openlocfilehash: 28e961aa20fb15b533f369ed436e2d8178d682801f6f6ce6a703e53a0c26ac01
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206912"
---
# <a name="solver-overview"></a>Panoramica del risolutore

![Solver Main](../../images/solver/MRTK_Solver_Main.png)

I risolutori sono componenti che facilitano il calcolo della posizione di un oggetto &'orientamento in base a un algoritmo predefinito. Un esempio può essere il posizionamento di un oggetto sulla superficie che attualmente raggiunge il raycast dello sguardo fisso dell'utente.

Inoltre, il sistema risolutore definisce in modo deterministico un ordine di operazioni per questi calcoli di trasformazione perché non esiste un modo affidabile per specificare in Unity l'ordine di aggiornamento dei componenti.

I risolutori offrono una gamma di comportamenti per collegare oggetti ad altri oggetti o sistemi. Un altro esempio è un oggetto tag-along che passa il mouse davanti all'utente (in base alla fotocamera). Un risolutore può anche essere collegato a un controller e a un oggetto per impostare il tag dell'oggetto lungo il controller. Tutti i risolutori possono essere impilati in modo sicuro, ad esempio un comportamento di tag-along + magnetismo della superficie + velocità.

## <a name="how-to-use-a-solver"></a>Come usare un risolutore

Il sistema risolutore è costituito da tre categorie di script:

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver): classe astratta di base da cui derivano tutti i risolutori. Offre monitoraggio dello stato, smussamento dei parametri e implementazione, integrazione automatica del sistema del risolutore e ordine di aggiornamento.
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler): imposta l'oggetto di riferimento su cui tenere traccia (ad esempio, la trasformazione principale della fotocamera, il raggio della mano e così via), gestisce la raccolta dei componenti del risolutore ed esegue l'aggiornamento nell'ordine corretto.

La terza categoria è il risolutore stesso. I risolutori seguenti forniscono i blocchi predefiniti per il comportamento di base:

* [`Orbital`](#orbital): blocca una posizione e un offset specificati dall'oggetto a cui si fa riferimento.
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize): ridimensiona per mantenere una dimensione costante rispetto alla visualizzazione dell'oggetto a cui si fa riferimento.
* [`RadialView`](#radialview): mantiene l'oggetto all'interno di un cono di visualizzazione di cui viene eseguito il cast dall'oggetto a cui si fa riferimento.
* [`Follow`](#follow): mantiene l'oggetto all'interno di un set di limiti definiti dall'utente dell'oggetto a cui si fa riferimento.
* [`InBetween`](#inbetween): mantiene un oggetto tra due oggetti tracciati.
* [`SurfaceMagnetism`](#surfacemagnetism): esegue il cast dei raggi sulle superfici del mondo e allinea l'oggetto a tale superficie.
* [`DirectionalIndicator`](#directionalindicator): determina la posizione e l'orientamento di un oggetto come indicatore direzionale. Dal punto di riferimento della destinazione rilevata SolverHandler, questo indicatore si orienta verso l'elemento DirectionalTarget fornito.
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum): applica accelerazione, velocità/attrito per simulare la velocità e la springiness di un oggetto spostato da altri risolutori/componenti.
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup): vincola l'oggetto per seguire le mani in un'area che non interseca il GameObject con le mani. Utile per contenuto interattivo vincolato a mano, ad esempio menu e così via. Questo risolutore è progettato per funzionare con [IMixedRealityHand,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) ma funziona anche con [IMixedRealityController.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController)
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup): deriva da HandConstraint, ma include la logica per verificare se il palmo è rivolto verso l'utente prima dell'attivazione. Questo risolutore funziona solo con i controller [IMixedRealityHand,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) con altri tipi di controller che si comporteranno esattamente come la relativa classe di base.

Per usare il sistema risolutore, è sufficiente aggiungere uno dei componenti elencati in precedenza a un GameObject. Poiché tutti i risolutori richiedono [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) un , ne verrà creato uno automaticamente da Unity.

> [!NOTE]
> Esempi di come usare il sistema solver sono disponibili nel file **SolverExamples.scene.**

## <a name="how-to-change-tracking-reference"></a>Informazioni di riferimento sul rilevamento delle modifiche

La *proprietà Tracked Target Type* del componente definisce il punto di riferimento che tutti i risolutori [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) useranno per calcolare i relativi algoritmi. Ad esempio, un tipo valore di con un componente semplice comporterà un raycast dalla testa e nella direzione dello sguardo dell'utente per la risoluzione della superficie che [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) viene raggiunto. I valori potenziali per `TrackedTargetType` la proprietà sono:

* *Head:* il punto di riferimento è la trasformazione della fotocamera principale
* *ControllerRay:* il punto di riferimento è [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) la trasformazione in un controller ,ad esempio origine del puntatore su un controller di movimento o un controller mano) che punta nella direzione del raggio della linea
  * Usare la `TrackedHandedness` proprietà per selezionare la preferenza di mano (ad esempio Left, Right, Both)
* *HandJoint:* il punto di riferimento è la trasformazione di un'giunzione della mano specifica
  * Usare la `TrackedHandedness` proprietà per selezionare la preferenza di mano (ad esempio Left, Right, Both)
  * Usare la  `TrackedHandJoint` proprietà per determinare la trasformazione congiunta da utilizzare
* *CustomOverride:* punto di riferimento dall'oggetto assegnato `TransformOverride`

> [!NOTE]
> Per entrambi i tipi *ControllerRay* e *HandJoint,* il gestore del risolutore tenterà di fornire prima la trasformazione controller/mano sinistra e quindi a destra se il primo non è disponibile o a meno che la proprietà non specifichi `TrackedHandedness` diversamente.

![Solver Tracked Object ](../../images/solver/TrackedObjectType-Example.gif) 
 *Esempio di varie proprietà associate a ogni TrackedTargetType*

> [!IMPORTANT]
> La maggior parte dei risolutori usa il vettore in avanti della destinazione di trasformazione rilevata fornita da `SolverHandler` . Quando si usa un *tipo di* destinazione tracciato Mano giunzione, il vettore in avanti del giunzione del palmo può puntare attraverso le dita e non attraverso il palmo. Ciò dipende dalla piattaforma che fornisce i dati del giunzione della mano. Per la simulazione Windows Mixed Reality input, è il vettore verso *l'alto* che punta verso l'alto attraverso il palmo (ad esempio il vettore verde è in alto, il vettore blu è in avanti).
>
> ![Vettore di avanzamento verso l'alto](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> Per risolvere questo problema, aggiornare la *proprietà Rotazione* aggiuntiva in in modo che<`SolverHandler` **90, 0, 0>**. Ciò garantisce che il vettore in avanti fornito ai risolutori punti attraverso il palmo e all'esterno dalla mano.
>
> ![Rotazione aggiuntiva](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> In alternativa, usare il tipo di destinazione *tracciata Controller Ray* per ottenere un comportamento simile per puntare con le mani.

## <a name="how-to-chain-solvers"></a>Come concatenare i risolutori

È possibile aggiungere più componenti `Solver` allo stesso GameObject concatenando così i relativi algoritmi. I `SolverHandler` componenti gestisce l'aggiornamento di tutti i risolutori nello stesso GameObject. Per impostazione `SolverHandler` predefinita, `GetComponents<Solver>()` le chiamate a Start restituiscono i risolutori nell'ordine in cui vengono visualizzati nel controllo.

Inoltre, l'impostazione della proprietà Updated *Linked Transform* su true indica che per salvare la posizione calcolata, l'orientamento e la scala & una variabile intermedia accessibile da tutti i risolutori (ad esempio, `Solver` `GoalPosition`). Se false, `Solver` aggiornerà direttamente la trasformazione del GameObject. Salvando le proprietà della trasformazione in una posizione intermedia, altri risolutori sono in grado di eseguire i calcoli a partire dalla variabile intermedia. Questo perché Unity non consente gli aggiornamenti a gameObject.transform per lo stack all'interno dello stesso frame.

> [!NOTE]
> Gli sviluppatori possono modificare l'ordine di esecuzione dei risolutori impostando direttamente `SolverHandler.Solvers` la proprietà .

## <a name="how-to-create-a-new-solver"></a>Come creare un nuovo risolutore

Tutti i risolutori devono ereditare dalla classe di base astratta , [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver) . I requisiti principali di un'estensione risolutore comportano l'override del `SolverUpdate` metodo . In questo metodo gli sviluppatori devono aggiornare le proprietà `GoalPosition` `GoalRotation` , e `GoalScale` ereditate ai valori desiderati. Inoltre, è in genere utile usare `SolverHandler.TransformTarget` come frame di riferimento desiderato dal consumer.

Il codice riportato di seguito fornisce un esempio di un nuovo componente risolutore denominato che posiziona l'oggetto collegato `InFront` 2 m davanti a `SolverHandler.TransformTarget` . Se è impostato dal consumer come , sarà la trasformazione della fotocamera e quindi questo Risolutore inserirà il GameObject collegato 2 m davanti a ogni fotogramma dello sguardo `SolverHandler.TrackedTargetType` [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) degli `SolverHandler.TransformTarget` utenti.

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

## <a name="solver-implementation-guides"></a>Guide all'implementazione del risolutore

### <a name="common-solver-properties"></a>Proprietà comuni del risolutore

Ogni componente risolutore ha un set di core di proprietà identiche che controllano il comportamento del risolutore principale.

Se *l'opzione Smoothing* è abilitata, il risolutore aggiornerà gradualmente la trasformazione del GameObject nel tempo in base ai valori calcolati. La velocità di questa modifica è determinata dalla proprietà *LerpTime* di ogni componente di trasformazione. Ad esempio, un valore *MoveLerpTime più* elevato comporta incrementi più lenti di spostamento tra i fotogrammi.

Se *MaintainScale* è abilitato, il risolutore utilizzerà la scala locale predefinita del GameObject.

![Proprietà del risolutore principale](../../images/solver/GeneralSolverProperties.png)  
*Proprietà comuni ereditate da tutti i componenti del risolutore*

### <a name="orbital"></a>Orbitale

La [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) classe è un componente tag-along che si comporta come i pianeta in un sistema solare. Questo risolutore garantisce che il GameObject collegato si aggira intorno alla trasformazione tracciata. Pertanto, se *il tipo di* destinazione tracciata di è impostato su , il GameObject si aggira intorno alla testa dell'utente con un offset [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) fisso applicato.

Gli sviluppatori possono modificare questo offset fisso per mantenere i menu o altri componenti della scena a livello visivo o a livello di attento e così via intorno a un utente. Questa operazione viene eseguita modificando le *proprietà Offset* locale e *World Offset.* La *proprietà Tipo di* orientamento determina la rotazione applicata all'oggetto se deve mantenere la rotazione originale o se deve sempre affrontare la fotocamera o il viso in qualsiasi trasformazione sta guidando la sua posizione e così via.

![Esempio orbital](../../images/solver/OrbitalExample.png)  
*Esempio orbital*

### <a name="radialview"></a>RadialView

è un altro componente di tag che mantiene una particolare parte di [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) un GameObject all'interno del frustum della visualizzazione dell'utente.

Le *proprietà Min & Max View Degrees* determinano le dimensioni di una parte del GameObject che devono essere sempre visualizzate.

Le *proprietà Min & Max Distance* (Distanza massima minima) determinano la distanza del GameObject da mantenere dall'utente. Ad esempio, se si avvicina  il GameObject con una distanza minima di 1 m, il GameObject viene allontanato per assicurarsi che non sia mai più vicino di 1 m all'utente.

In genere, [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) viene usato insieme a *Tracked Target Type* impostato su in modo che il componente [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) segua lo sguardo dell'utente. Tuttavia, questo componente può funzionare per essere mantenuto *nella "visualizzazione"* di qualsiasi *tipo di destinazione rilevata.*

![Esempio di RadialView](../../images/solver/RadialViewExample.png)  
*Esempio di RadialView*

### <a name="follow"></a>Segui

La [`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow) classe posiziona un elemento davanti all'oggetto della destinazione rilevata rispetto al relativo asse in avanti locale. L'elemento può essere vincolato in modo libero (ovvero tag-along) in modo che non segua finché la destinazione rilevata non si sposta oltre i limiti definiti dall'utente.

Funziona in modo analogo al risolutore RadialView, con controlli aggiuntivi per gestire Max *Horizontal & Vertical View Degrees* e meccanismi per modificare l'orientamento dell'oggetto. 

![Seguire le proprietà](../../images/solver/FollowExample.png)  
*Seguire le proprietà*

![Seguire la scena di esempio](../../images/solver/FollowExampleScene.gif)  
*Seguire la scena di esempio (Assets/MRTK/Examples/Demos/Solvers/Scenes/FollowSolverExample.unity)*

### <a name="inbetween"></a>Inbetween

La [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) classe manterà il GameObject collegato tra due trasformazioni. Questi due endpoint di trasformazione sono definiti dal tipo di destinazione tracciato del GameObject e dalla proprietà [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)  [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) Second *Tracked Target Type del* componente. In genere, entrambi i tipi verranno impostati su [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride) e i valori e `SolverHandler.TransformOverride` `InBetween.SecondTransformOverride` risultanti verranno impostati su due endpoint monitorati.

In fase di esecuzione, il componente creerà un altro componente basato sulle proprietà Secondo tipo di destinazione tracciato e [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) Secondo override *trasformazione.* 

definisce dove lungo la linea tra due trasformazioni l'oggetto deve essere posizionato con 0,5 a metà, 1,0 alla prima trasformazione e 0,0 in corrispondenza della seconda `PartwayOffset` trasformazione.

![Esempio inBetween](../../images/solver/InBetweenExample.png)  
*Esempio di uso del risolutore InBetween per mantenere l'oggetto tra due trasformazioni*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

Il metodo esegue un raycast su un set di superfici LayerMask e posiziona [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) il GameObject in quel punto di contatto.

*L'offset normale* della superficie posiziona il GameObject a una distanza impostata in metri dalla superficie nella direzione della normale in corrispondenza del punto di attacco sulla superficie.

Al contrario, Surface *Ray Offset* posiziona il GameObject a una distanza impostata in metri dalla superficie, ma nella direzione opposta del raycast eseguito. Pertanto, se il raycast è lo sguardo dell'utente, il GameObject si sposterà più vicino lungo la linea dal punto di hit sulla superficie alla fotocamera.

La *modalità di* orientamento determina il tipo di rotazione da applicare in relazione alla normale sulla superficie.

* *Nessuno -* Nessuna rotazione applicata
* *TrackedTarget: l'oggetto* affronta la trasformazione rilevata che guida il raycast
* *SurfaceNormal:* l'oggetto verrà allineato in base alla normale in corrispondenza del punto di attacco sulla superficie
* *Blended* : l'oggetto verrà allineato in base alla normale in corrispondenza del punto di hit point sulla superficie E in base alla trasformazione rilevata.

Per forzare il GameObject associato a rimanere verticale in qualsiasi modalità diversa da *None,* abilitare *Mantieni orientamento verticale.*

> [!NOTE]
> Usare la *proprietà Blend orientamento* per controllare il bilanciamento tra i fattori di rotazione quando *Modalità* orientamento è impostato su *Blended*. Un valore pari a 0,0 avrà un orientamento interamente basato sulla modalità *TrackedTarget* e un valore pari a 1,0 avrà l'orientamento interamente guidato da *SurfaceNormal.*

![Esempio di SurfaceMagnetism](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>Determinazione delle superfici che possono essere raggiunto

Quando si aggiunge [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) un componente a un GameObject, è importante considerare il livello del GameObject e i relativi elementi figlio, se presenti. Il componente funziona eseguendo vari tipi di raycast per determinare la superficie su cui "magnete" si opera. Se il GameObject del risolutore ha un collisore su uno dei livelli elencati nella proprietà di , è probabile che il raycast raggiri se stesso causando il collegamento del GameObject al proprio punto di `MagneticSurfaces` `SurfaceMagnetism` collisore. Questo comportamento dispari può essere evitato impostando il GameObject principale e tutti gli elementi figlio sul livello *Ignora raycast* o modificando la `MagneticSurfaces` matrice LayerMask in modo appropriato.

Al contrario, un GameObject non entra in conflitto con le superfici di [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) un livello non elencato nella proprietà `MagneticSurfaces` . È in genere consigliabile posizionare tutte le superfici desiderate su un livello dedicato,ad esempio *Superfici )* e impostando la `MagneticSurfaces` proprietà solo su questo livello.  *L'uso del* *valore predefinito o di* tutti gli elementi può comportare l'uso di componenti o cursori dell'interfaccia utente che contribuiscono al risolutore.

Infine, le superfici più di quelle `MaxRaycastDistance` dell'impostazione della proprietà verranno ignorate dai `SurfaceMagnetism` raycast.

### <a name="directionalindicator"></a>DirectionalIndicator

La [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) classe è un componente tag-along che si orienta verso la direzione di un punto desiderato nello spazio.

Usato più di frequente quando *il tipo di destinazione tracciata* di è impostato su [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) . In questo modo, un componente dell'esperienza utente con il risolutore indica a un utente di esaminare [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator)  il punto desiderato nello spazio.

Il punto desiderato nello spazio viene determinato tramite la *proprietà Destinazione direzionale.*

Se la destinazione direzionale è visualizzabile dall'utente o qualsiasi frame di riferimento impostato in , questo risolutore disabiliterà tutti i [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) componenti sottostanti. Se non è visualizzabile, tutti gli elementi verranno abilitati nell'indicatore.

Le dimensioni dell'indicatore si ridurranno più vicino all'acquisizione della destinazione *direzionale* nella fov.

* *Scala indicatore minima:* scala minima per l'oggetto indicatore
* *Max Indicator Scale (Scala massima* indicatore) - Scala massima per l'oggetto indicatore

* *Fattore di scala della* visibilità: moltiplicatore per  aumentare o ridurre la fov che determina se il punto di destinazione direzionale è visualizzabile o meno
* *View Offset (Offset* visualizzazione) - Dal punto di vista del frame di riferimento (ad esempio camera possibilmente), questa proprietà definisce quanto deve essere lontano l'oggetto dalla parte centrale del viewport nella direzione dell'indicatore.

![Proprietà indicatore direzionale](../../images/solver/DirectionalIndicatorExample.png)  
*Proprietà indicatore direzionale*

![Scena di esempio indicatore direzionale](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*Scena di esempio indicatore direzionale (Assets/MRTK/Examples/Demos/Solvers/Scenes/DirectionalIndicatorSolverExample.unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>Menu mano con HandConstraint e HandConstraintPalmUp

![Esempio di esperienza utente del menu a mano](../../images/solver/MRTK_UX_HandMenu.png)

Il comportamento fornisce un risolutore che vincola l'oggetto tracciato a un'area sicura per il contenuto vincolato a mano (ad esempio interfaccia utente [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) manuale, menu e così via). Cassaforte aree sono considerate aree che non si intersecano con la mano. È inclusa anche una classe derivata di denominata per illustrare un comportamento comune di attivazione dell'oggetto tracciato dal risolutore quando il [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) palmo è rivolto verso l'utente.

[Vedere la pagina Hand Menu (Menu mano)](../hand-menu.md) per gli esempi d'uso del risolutore Hand Constraint (Vincolo mano) per creare menu a mano.

## <a name="see-also"></a>Vedi anche

* [Tracciamento delle mani](../../input/hand-tracking.md)
* [Sguardo fisso](../../input/gaze.md)
