---
title: ElasticSystem
description: documentazione relativa alla simulazione di elastici in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, ElasticsSystem,
ms.openlocfilehash: b58f22b7481aa2f0e016b0710d5953a7f6f2155b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782686"
---
# <a name="elastic-system-experimental"></a>Sistema elastico (sperimentale)

![Sistema elastico](../Images/Elastics/Elastics_Main1.gif)

MRTK è dotato di un sistema di simulazione elastica che include una vasta gamma di sottoclassi estendibili e flessibili, che offrono associazioni per le primavere quaternioni a 4 dimensioni, sorgenti di volumi tridimensionali e semplici sistemi Spring lineari.

Attualmente i componenti MRTK seguenti che supportano [Elastics Manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) possono sfruttare le funzionalità di elasticità:

- [Controllo dei limiti](../README_BoundsControl.md)
- [Manipolatore di oggetti](../README_ObjectManipulator.md)

## <a name="elastics-manager"></a>Gestione elastici

![System2 elastico](../Images/Elastics/Elastics_Main.gif)

I processi di gestione elastici hanno passato le trasformazioni e le alimentano al sistema elastico.

L'abilitazione di elastici per i componenti personalizzati può essere eseguita in due passaggi:

1. Chiamata al metodo Initialize all'avvio della manipolazione, aggiornamento del sistema con la trasformazione host corrente.
1. Esecuzione di query su ApplyHostTransform ogni volta che è necessario eseguire un calcolo elastico sulla trasformazione di destinazione aggiornata.

Si noti che gli elastici continueranno a simulare una volta terminata la manipolazione (tramite il ciclo di aggiornamento di gestione elastici). Per bloccare il comportamento, l'aggiornamento automatico degli elastici [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) può essere impostato su false.

Per impostazione predefinita, il componente di gestione elastici, quando viene aggiunto a un oggetto gioco, non avrà elastici abilitati per qualsiasi tipo di trasformazioni.
Il campo `Manipulation types using elastic feedback` deve essere abilitato per tipi di trasformazione specifici per creare gli extent e la configurazione elastici per il tipo selezionato.

### <a name="elastics-configurations"></a>Configurazioni elastiche

Analogamente alle configurazioni del controllo dei limiti, il gestore elastico include un set di oggetti di configurazione che possono essere archiviati come oggetti [configurabili](../README_BoundsControl.md#configuration-objects)tramite script e condivisi tra istanze diverse o prefabbricati. Le configurazioni possono essere condivise e collegate come singoli file di asset gestibili tramite script o asset annidabili tramite script all'interno di prefabbricati. È anche possibile definire altre configurazioni direttamente nell'istanza senza eseguire il collegamento a un asset con script esterno o annidato.

Il controllo di gestione elastici indicherà se una configurazione è condivisa o inline come parte dell'istanza corrente visualizzando un messaggio nel controllo proprietà. Inoltre, le istanze condivise non saranno modificabili direttamente nella finestra delle proprietà di Elastics Manager, ma l'asset a cui è collegato deve essere direttamente modificati per evitare modifiche accidentali nelle configurazioni condivise.

Elastics Manager offre opzioni di oggetti di configurazione per i tipi di trasformazione seguenti, ognuno dei quali è rappresentato da un [oggetto di configurazione elastica](#elastic-configuration-object):

- Traslazione elastico
- Elasticità rotazione
- Scalabilità elastica

#### <a name="elastic-configuration-object"></a>Oggetto di configurazione elastica

Una configurazione elastica definisce le proprietà per un sistema differenziale di oscillatore armonico smorzato.
Le proprietà seguenti possono essere modificate, ma sono già disponibili con un set di valori predefiniti in MRTK:

- **Mass**: massa dell'elemento Oscillator simulato.
- **HandK**: costante Spring della mano.
- **EndK**: costante Spring Cap end.
- **SnapK**: costante Spring del punto di aggancio.
- **Trascinare**: fattore di trascinamento, proporzionale alla velocità.

### <a name="elastics-extents"></a>Extent elastici

Le impostazioni degli extent elastici variano a seconda del tipo di manipolazione. La conversione e la scala sono rappresentate da [extent elastici del volume](#volume-elastic-extent) e la rotazione viene rappresentata da un [extent elastico quaternione](#quaternion-elastic-extent).

#### <a name="volume-elastic-extent"></a>Extent elastico volume

Gli extent del volume definiscono uno spazio tridimensionale in cui l'oscillatore armonico smorzato è libero di spostarsi.

![Limiti di estensione del volume elastico](../Images/Elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds**: rappresenta i limiti inferiori dello spazio elastico.
- **UseBounds**: indica se i limiti di estensione devono essere rispettati dal sistema. Se true, quando l'iterazione corrente della posizione di destinazione è al di fuori dei limiti di estensione, viene applicata la forza fine.
- **Ancoraggio**: punta all'interno dello spazio in cui il sistema si blocca.
- **RepeatSnapPoints**: ripete i punti di aggancio all'infinito. I punti di blocco esistenti fungeranno da modulo in cui i punti di allineamento effettivi vengono mappati ai multipli integer più vicini di ogni punto di blocco.
- **SnapRadius**: distanza alla quale i punti di blocco iniziano a forzare la primavera.

![Griglia di snap-in volume elastico](../Images/Elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Extent elastico Quaternion

Gli extent Quaternion definiscono uno spazio di rotazione quattro dimensioni in cui l'oscillatore armonico smorzato è libero di ruotare.

![Esempio di rotazione elastica](../Images/Elastics/Elastics_Rotation.gif)

- **Ancoraggio**: angoli di Eulero in cui il sistema si blocca.
- **RepeatSnapPoints**: ripete i punti di aggancio. I punti di blocco esistenti fungeranno da modulo in cui i punti di allineamento effettivi vengono mappati ai multipli integer più vicini di ogni punto di blocco.
- **SnapRadius**: angolo di arco in corrispondenza del quale i punti di allineamento iniziano a forzare la molla in gradi di Eulero.

## <a name="elastics-example-scene"></a>Scena di esempio elastici

È possibile trovare esempi di configurazioni elastiche nella `ElasticSystemExample` scena.

![Scena di esempio elastici](../Images/Elastics/Elastics_Example_Scene.png)
