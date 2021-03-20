---
title: ElasticSystem
description: documentazione relativa alla simulazione di elastici in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, ElasticsSystem,
ms.openlocfilehash: c605bc59bb47ca30042911afb895ab0ff9a507ab
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681804"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="3f82b-104">Sistema elastico (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="3f82b-104">Elastic system (experimental)</span></span>

![Sistema elastico](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="3f82b-106">MRTK è dotato di un sistema di simulazione elastica che include una vasta gamma di sottoclassi estendibili e flessibili, che offrono associazioni per le primavere quaternioni a 4 dimensioni, sorgenti di volumi tridimensionali e semplici sistemi Spring lineari.</span><span class="sxs-lookup"><span data-stu-id="3f82b-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="3f82b-107">Attualmente i componenti MRTK seguenti che supportano [Elastics Manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) possono sfruttare le funzionalità di elasticità:</span><span class="sxs-lookup"><span data-stu-id="3f82b-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="3f82b-108">Controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="3f82b-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="3f82b-109">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="3f82b-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="3f82b-110">Gestione elastici</span><span class="sxs-lookup"><span data-stu-id="3f82b-110">Elastics manager</span></span>

![System2 elastico](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="3f82b-112">I processi di gestione elastici hanno passato le trasformazioni e le alimentano al sistema elastico.</span><span class="sxs-lookup"><span data-stu-id="3f82b-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="3f82b-113">L'abilitazione di elastici per i componenti personalizzati può essere eseguita in due passaggi:</span><span class="sxs-lookup"><span data-stu-id="3f82b-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="3f82b-114">Chiamata al metodo Initialize all'avvio della manipolazione, aggiornamento del sistema con la trasformazione host corrente.</span><span class="sxs-lookup"><span data-stu-id="3f82b-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="3f82b-115">Esecuzione di query su ApplyHostTransform ogni volta che è necessario eseguire un calcolo elastico sulla trasformazione di destinazione aggiornata.</span><span class="sxs-lookup"><span data-stu-id="3f82b-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="3f82b-116">Si noti che gli elastici continueranno a simulare una volta terminata la manipolazione (tramite il ciclo di aggiornamento di gestione elastici).</span><span class="sxs-lookup"><span data-stu-id="3f82b-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="3f82b-117">Per bloccare il comportamento, l'aggiornamento automatico degli elastici [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) può essere impostato su false.</span><span class="sxs-lookup"><span data-stu-id="3f82b-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="3f82b-118">Per impostazione predefinita, il componente di gestione elastici, quando viene aggiunto a un oggetto gioco, non avrà elastici abilitati per qualsiasi tipo di trasformazioni.</span><span class="sxs-lookup"><span data-stu-id="3f82b-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="3f82b-119">Il campo `Manipulation types using elastic feedback` deve essere abilitato per tipi di trasformazione specifici per creare gli extent e la configurazione elastici per il tipo selezionato.</span><span class="sxs-lookup"><span data-stu-id="3f82b-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="3f82b-120">Configurazioni elastiche</span><span class="sxs-lookup"><span data-stu-id="3f82b-120">Elastics configurations</span></span>

<span data-ttu-id="3f82b-121">Analogamente alle configurazioni del controllo dei limiti, il gestore elastico include un set di oggetti di configurazione che possono essere archiviati come oggetti [configurabili](../ux-building-blocks/bounds-control.md#configuration-objects)tramite script e condivisi tra istanze diverse o prefabbricati.</span><span class="sxs-lookup"><span data-stu-id="3f82b-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="3f82b-122">Le configurazioni possono essere condivise e collegate come singoli file di asset gestibili tramite script o asset annidabili tramite script all'interno di prefabbricati.</span><span class="sxs-lookup"><span data-stu-id="3f82b-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="3f82b-123">È anche possibile definire altre configurazioni direttamente nell'istanza senza eseguire il collegamento a un asset con script esterno o annidato.</span><span class="sxs-lookup"><span data-stu-id="3f82b-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="3f82b-124">Il controllo di gestione elastici indicherà se una configurazione è condivisa o inline come parte dell'istanza corrente visualizzando un messaggio nel controllo proprietà.</span><span class="sxs-lookup"><span data-stu-id="3f82b-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="3f82b-125">Inoltre, le istanze condivise non saranno modificabili direttamente nella finestra delle proprietà di Elastics Manager, ma l'asset a cui è collegato deve essere direttamente modificati per evitare modifiche accidentali nelle configurazioni condivise.</span><span class="sxs-lookup"><span data-stu-id="3f82b-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="3f82b-126">Elastics Manager offre opzioni di oggetti di configurazione per i tipi di trasformazione seguenti, ognuno dei quali è rappresentato da un [oggetto di configurazione elastica](#elastic-configuration-object):</span><span class="sxs-lookup"><span data-stu-id="3f82b-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="3f82b-127">Traslazione elastico</span><span class="sxs-lookup"><span data-stu-id="3f82b-127">Translation Elastic</span></span>
- <span data-ttu-id="3f82b-128">Elasticità rotazione</span><span class="sxs-lookup"><span data-stu-id="3f82b-128">Rotation Elastic</span></span>
- <span data-ttu-id="3f82b-129">Scalabilità elastica</span><span class="sxs-lookup"><span data-stu-id="3f82b-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="3f82b-130">Oggetto di configurazione elastica</span><span class="sxs-lookup"><span data-stu-id="3f82b-130">Elastic configuration object</span></span>

<span data-ttu-id="3f82b-131">Una configurazione elastica definisce le proprietà per un sistema differenziale di oscillatore armonico smorzato.</span><span class="sxs-lookup"><span data-stu-id="3f82b-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="3f82b-132">Le proprietà seguenti possono essere modificate, ma sono già disponibili con un set di valori predefiniti in MRTK:</span><span class="sxs-lookup"><span data-stu-id="3f82b-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="3f82b-133">**Mass**: massa dell'elemento Oscillator simulato.</span><span class="sxs-lookup"><span data-stu-id="3f82b-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="3f82b-134">**HandK**: costante Spring della mano.</span><span class="sxs-lookup"><span data-stu-id="3f82b-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="3f82b-135">**EndK**: costante Spring Cap end.</span><span class="sxs-lookup"><span data-stu-id="3f82b-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="3f82b-136">**SnapK**: costante Spring del punto di aggancio.</span><span class="sxs-lookup"><span data-stu-id="3f82b-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="3f82b-137">**Trascinare**: fattore di trascinamento, proporzionale alla velocità.</span><span class="sxs-lookup"><span data-stu-id="3f82b-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="3f82b-138">Extent elastici</span><span class="sxs-lookup"><span data-stu-id="3f82b-138">Elastics extents</span></span>

<span data-ttu-id="3f82b-139">Le impostazioni degli extent elastici variano a seconda del tipo di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="3f82b-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="3f82b-140">La conversione e la scala sono rappresentate da [extent elastici del volume](#volume-elastic-extent) e la rotazione viene rappresentata da un [extent elastico quaternione](#quaternion-elastic-extent).</span><span class="sxs-lookup"><span data-stu-id="3f82b-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="3f82b-141">Extent elastico volume</span><span class="sxs-lookup"><span data-stu-id="3f82b-141">Volume elastic extent</span></span>

<span data-ttu-id="3f82b-142">Gli extent del volume definiscono uno spazio tridimensionale in cui l'oscillatore armonico smorzato è libero di spostarsi.</span><span class="sxs-lookup"><span data-stu-id="3f82b-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Limiti di estensione del volume elastico](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="3f82b-144">**StretchBounds**: rappresenta i limiti inferiori dello spazio elastico.</span><span class="sxs-lookup"><span data-stu-id="3f82b-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="3f82b-145">**UseBounds**: indica se i limiti di estensione devono essere rispettati dal sistema.</span><span class="sxs-lookup"><span data-stu-id="3f82b-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="3f82b-146">Se true, quando l'iterazione corrente della posizione di destinazione è al di fuori dei limiti di estensione, viene applicata la forza fine.</span><span class="sxs-lookup"><span data-stu-id="3f82b-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="3f82b-147">**Ancoraggio**: punta all'interno dello spazio in cui il sistema si blocca.</span><span class="sxs-lookup"><span data-stu-id="3f82b-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="3f82b-148">**RepeatSnapPoints**: ripete i punti di aggancio all'infinito.</span><span class="sxs-lookup"><span data-stu-id="3f82b-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="3f82b-149">I punti di blocco esistenti fungeranno da modulo in cui i punti di allineamento effettivi vengono mappati ai multipli integer più vicini di ogni punto di blocco.</span><span class="sxs-lookup"><span data-stu-id="3f82b-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="3f82b-150">**SnapRadius**: distanza alla quale i punti di blocco iniziano a forzare la primavera.</span><span class="sxs-lookup"><span data-stu-id="3f82b-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Griglia di snap-in volume elastico](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="3f82b-152">Extent elastico Quaternion</span><span class="sxs-lookup"><span data-stu-id="3f82b-152">Quaternion elastic extent</span></span>

<span data-ttu-id="3f82b-153">Gli extent Quaternion definiscono uno spazio di rotazione quattro dimensioni in cui l'oscillatore armonico smorzato è libero di ruotare.</span><span class="sxs-lookup"><span data-stu-id="3f82b-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Esempio di rotazione elastica](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="3f82b-155">**Ancoraggio**: angoli di Eulero in cui il sistema si blocca.</span><span class="sxs-lookup"><span data-stu-id="3f82b-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="3f82b-156">**RepeatSnapPoints**: ripete i punti di aggancio.</span><span class="sxs-lookup"><span data-stu-id="3f82b-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="3f82b-157">I punti di blocco esistenti fungeranno da modulo in cui i punti di allineamento effettivi vengono mappati ai multipli integer più vicini di ogni punto di blocco.</span><span class="sxs-lookup"><span data-stu-id="3f82b-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="3f82b-158">**SnapRadius**: angolo di arco in corrispondenza del quale i punti di allineamento iniziano a forzare la molla in gradi di Eulero.</span><span class="sxs-lookup"><span data-stu-id="3f82b-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="3f82b-159">Scena di esempio elastici</span><span class="sxs-lookup"><span data-stu-id="3f82b-159">Elastics example scene</span></span>

<span data-ttu-id="3f82b-160">È possibile trovare esempi di configurazioni elastiche nella `ElasticSystemExample` scena.</span><span class="sxs-lookup"><span data-stu-id="3f82b-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Scena di esempio elastici](../images/elastics/Elastics_Example_Scene.png)
