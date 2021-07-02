---
title: Sistema elastico
description: Documentazione correlata alla simulazione degli elastici in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, ElasticsSystem,
ms.openlocfilehash: 44110cac9ac5aadb7b5e680f18a5e93f43efce12
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177793"
---
# <a name="elastic-system"></a><span data-ttu-id="57be2-104">Sistema elastico</span><span class="sxs-lookup"><span data-stu-id="57be2-104">Elastic system</span></span>

![Sistema elastico](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="57be2-106">MRTK è dotato di un sistema di simulazione elastico che include un'ampia gamma di sottoclassi estendibili e flessibili, offrendo associazioni per le molle quaternione 4-dimensionali, le molle a volume tridimensionale e i semplici sistemi a sorgente lineare.</span><span class="sxs-lookup"><span data-stu-id="57be2-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="57be2-107">Attualmente i componenti MRTK seguenti che supportano il gestore [elastici](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) possono sfruttare la funzionalità elastica:</span><span class="sxs-lookup"><span data-stu-id="57be2-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="57be2-108">Controllo Limiti</span><span class="sxs-lookup"><span data-stu-id="57be2-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="57be2-109">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="57be2-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="57be2-110">Gestore elastici</span><span class="sxs-lookup"><span data-stu-id="57be2-110">Elastics manager</span></span>

![Sistema elastico 2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="57be2-112">Il gestore elastici elabora le trasformazioni passate e le alimenta nel sistema elastico.</span><span class="sxs-lookup"><span data-stu-id="57be2-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="57be2-113">L'abilitazione degli elastici per i componenti personalizzati può essere ottenuta in due passaggi:</span><span class="sxs-lookup"><span data-stu-id="57be2-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="57be2-114">Chiamata del metodo Initialize all'avvio della manipolazione, aggiornamento del sistema con la trasformazione host corrente.</span><span class="sxs-lookup"><span data-stu-id="57be2-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="57be2-115">Esecuzione di query su ApplyHostTransform ogni volta che è necessario eseguire un calcolo elastico sulla trasformazione di destinazione aggiornata.</span><span class="sxs-lookup"><span data-stu-id="57be2-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="57be2-116">Si noti che gli elastici continueranno a simulare al termine della manipolazione (tramite il ciclo di aggiornamento del gestore elastici).</span><span class="sxs-lookup"><span data-stu-id="57be2-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="57be2-117">Per bloccare il comportamento, l'aggiornamento automatico degli elastici [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) può essere impostato su false.</span><span class="sxs-lookup"><span data-stu-id="57be2-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="57be2-118">Per impostazione predefinita, il componente di gestione elastici, quando viene aggiunto a un oggetto gioco, non ha elastici abilitati per alcun tipo di trasformazione.</span><span class="sxs-lookup"><span data-stu-id="57be2-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="57be2-119">Il campo `Manipulation types using elastic feedback` deve essere abilitato per tipi di trasformazione specifici per creare la configurazione degli elastici e gli extent per il tipo selezionato.</span><span class="sxs-lookup"><span data-stu-id="57be2-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="57be2-120">Configurazioni elastiche</span><span class="sxs-lookup"><span data-stu-id="57be2-120">Elastics configurations</span></span>

<span data-ttu-id="57be2-121">Analogamente alle [configurazioni di](../ux-building-blocks/bounds-control.md#configuration-objects)controllo dei limiti, la gestione elastica include un set di oggetti di configurazione che possono essere archiviati come oggetti di cui è possibile eseguire script e condivisi tra istanze o prefab diversi.</span><span class="sxs-lookup"><span data-stu-id="57be2-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="57be2-122">Le configurazioni possono essere condivise e collegate come singoli file di asset modificabili tramite script o asset annidati che possono essere script all'interno di prefab.</span><span class="sxs-lookup"><span data-stu-id="57be2-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="57be2-123">È anche possibile definire altre configurazioni direttamente nell'istanza senza collegarsi a un asset esterno o annidabile tramite script.</span><span class="sxs-lookup"><span data-stu-id="57be2-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="57be2-124">Il controllo di gestione elastici indicherà se una configurazione è condivisa o inline come parte dell'istanza corrente visualizzando un messaggio nella finestra di ispezione proprietà.</span><span class="sxs-lookup"><span data-stu-id="57be2-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="57be2-125">Inoltre, le istanze condivise non saranno modificabili direttamente nella finestra delle proprietà di Gestione elastici, ma l'asset a cui si collega deve essere modificato direttamente per evitare modifiche accidentali nelle configurazioni condivise.</span><span class="sxs-lookup"><span data-stu-id="57be2-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="57be2-126">Gestione elastici offre opzioni di oggetti di configurazione per i tipi di trasformazione seguenti, ognuno dei quali rappresentato da un oggetto [di configurazione elastico](#elastic-configuration-object):</span><span class="sxs-lookup"><span data-stu-id="57be2-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="57be2-127">Elastico di traduzione</span><span class="sxs-lookup"><span data-stu-id="57be2-127">Translation Elastic</span></span>
- <span data-ttu-id="57be2-128">Elastico di rotazione</span><span class="sxs-lookup"><span data-stu-id="57be2-128">Rotation Elastic</span></span>
- <span data-ttu-id="57be2-129">Scalabilità elastica</span><span class="sxs-lookup"><span data-stu-id="57be2-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="57be2-130">Oggetto di configurazione elastico</span><span class="sxs-lookup"><span data-stu-id="57be2-130">Elastic configuration object</span></span>

<span data-ttu-id="57be2-131">Una configurazione elastica definisce le proprietà per un sistema differenziale dell'oscillatore armonico smorzato.</span><span class="sxs-lookup"><span data-stu-id="57be2-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="57be2-132">Le proprietà seguenti possono essere modificate, ma sono già disponibili con un set di impostazioni predefinite in MRTK:</span><span class="sxs-lookup"><span data-stu-id="57be2-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="57be2-133">**Massa:** massa dell'elemento oscillatore simulato.</span><span class="sxs-lookup"><span data-stu-id="57be2-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="57be2-134">**HandK:** costante della mano a molle.</span><span class="sxs-lookup"><span data-stu-id="57be2-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="57be2-135">**EndK:** costante end cap spring.</span><span class="sxs-lookup"><span data-stu-id="57be2-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="57be2-136">**SnapK:** costante di molle del punto di snap.</span><span class="sxs-lookup"><span data-stu-id="57be2-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="57be2-137">**Trascinare**: fattore di trascinamento/smorzatore, proporzionale alla velocità.</span><span class="sxs-lookup"><span data-stu-id="57be2-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="57be2-138">Extent elastici</span><span class="sxs-lookup"><span data-stu-id="57be2-138">Elastics extents</span></span>

<span data-ttu-id="57be2-139">Le impostazioni degli extent elastici variano a seconda del tipo di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="57be2-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="57be2-140">La traslazione e la scala sono rappresentate da [extent elastici del volume](#volume-elastic-extent) e la rotazione è rappresentata da un extent [elastico quaternione.](#quaternion-elastic-extent)</span><span class="sxs-lookup"><span data-stu-id="57be2-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="57be2-141">Extent elastico del volume</span><span class="sxs-lookup"><span data-stu-id="57be2-141">Volume elastic extent</span></span>

<span data-ttu-id="57be2-142">Gli extent di volume definiscono uno spazio tridimensionale in cui l'oscillatore armonico smorzato è libero di spostarsi.</span><span class="sxs-lookup"><span data-stu-id="57be2-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Limiti di estensione del volume elastico](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="57be2-144">**StretchBounds**: rappresenta i limiti inferiori dello spazio elastico.</span><span class="sxs-lookup"><span data-stu-id="57be2-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="57be2-145">**UseBounds:** indica se i limiti di estensione devono essere rispettati dal sistema.</span><span class="sxs-lookup"><span data-stu-id="57be2-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="57be2-146">Se true, quando l'iterazione corrente della posizione di destinazione non rientra nei limiti di estensione, verrà applicata la forza finale.</span><span class="sxs-lookup"><span data-stu-id="57be2-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="57be2-147">**SnapPoints**: punti all'interno dello spazio a cui verrà allineato il sistema.</span><span class="sxs-lookup"><span data-stu-id="57be2-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="57be2-148">**RepeatSnapPoints**: ripete i punti di ancoraggio all'infinito.</span><span class="sxs-lookup"><span data-stu-id="57be2-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="57be2-149">I punti di snap esistenti fungeranno da modulo in cui i punti di snap effettivi vengono mappati ai multipli interi più vicini di ogni punto di snap.</span><span class="sxs-lookup"><span data-stu-id="57be2-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="57be2-150">**SnapRadius:** distanza da cui i punti di snap iniziano a forzare la sorgente.</span><span class="sxs-lookup"><span data-stu-id="57be2-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Griglia di snap del volume elastico](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="57be2-152">Extent elastico quaternione</span><span class="sxs-lookup"><span data-stu-id="57be2-152">Quaternion elastic extent</span></span>

<span data-ttu-id="57be2-153">Gli extent quaternione definiscono uno spazio di rotazione quattro dimensionale in cui l'oscillatore armonico smorzato è libero di ruotare.</span><span class="sxs-lookup"><span data-stu-id="57be2-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Esempio di rotazione elastica](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="57be2-155">**SnapPoints**: angoli euleri a cui si aggancia il sistema.</span><span class="sxs-lookup"><span data-stu-id="57be2-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="57be2-156">**RepeatSnapPoints**: ripete i punti di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="57be2-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="57be2-157">I punti di snap esistenti fungeranno da modulo in cui i punti di snap effettivi vengono mappati ai multipli interi più vicini di ogni punto di snap.</span><span class="sxs-lookup"><span data-stu-id="57be2-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="57be2-158">**SnapRadius:** arco angolare in corrispondenza del quale i punti di snap iniziano forzando la primavera in gradi eulero.</span><span class="sxs-lookup"><span data-stu-id="57be2-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="57be2-159">Scena di esempio elastici</span><span class="sxs-lookup"><span data-stu-id="57be2-159">Elastics example scene</span></span>

<span data-ttu-id="57be2-160">Nella scena sono disponibili esempi di configurazioni `ElasticSystemExample` elastiche.</span><span class="sxs-lookup"><span data-stu-id="57be2-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Scena di esempio elastici](../images/elastics/Elastics_Example_Scene.png)
