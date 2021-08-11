---
title: Sistema elastico
description: Documentazione relativa alla simulazione di elastici in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, ElasticsSystem,
ms.openlocfilehash: e34b9ea68bfbdc7b7f285686565a1e049ba58ad8677b16e915a2db8272ec1cbe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217903"
---
# <a name="elastic-system"></a>Sistema elastico

![Sistema elastico](../images/elastics/Elastics_Main1.gif)

MRTK è dotato di un sistema di simulazione elastico che include un'ampia gamma di sottoclassi estendibili e flessibili, che offrono binding per quaternione tridimensionale, un volume tridimensionale e semplici sistemi a sorgente lineare.

Attualmente i componenti MRTK seguenti che supportano il gestore [elastici](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) possono sfruttare le funzionalità elastiche:

- [Controllo Limiti](../ux-building-blocks/bounds-control.md)
- [Manipolatore di oggetti](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Gestore elastici

![Elastic System2](../images/elastics/Elastics_Main.gif)

Il gestore elastici elabora le trasformazioni passate e le inseri nel sistema elastico.

L'abilitazione degli elastici per i componenti personalizzati può essere ottenuta in due passaggi:

1. Chiamata del metodo Initialize all'avvio della manipolazione, aggiornamento del sistema con la trasformazione host corrente.
1. Esecuzione di query su ApplyHostTransform ogni volta che è necessario eseguire un calcolo elastico sulla trasformazione di destinazione aggiornata.

Si noti che gli elastici continueranno a simulare al termine della manipolazione (tramite il ciclo di aggiornamento del gestore elastici). Per bloccare il comportamento, l'aggiornamento automatico [enableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) degli elastici può essere impostato su false.

Per impostazione predefinita, il componente di gestione elastici, quando viene aggiunto a un oggetto gioco, non ha elastici abilitati per alcun tipo di trasformazione.
Il campo `Manipulation types using elastic feedback` deve essere abilitato per tipi di trasformazione specifici per creare la configurazione elastica e gli extent per il tipo selezionato.

### <a name="elastics-configurations"></a>Configurazioni elastiche

Analogamente alle [configurazioni di](../ux-building-blocks/bounds-control.md#configuration-objects)controllo dei limiti, la gestione elastica include un set di oggetti di configurazione che possono essere archiviati come oggetti gestibili da script e condivisi tra istanze o prefab diversi. Le configurazioni possono essere condivise e collegate come singoli file di asset gestibili tramite script o asset annidati gestibili tramite script all'interno di prefab. È anche possibile definire altre configurazioni direttamente nell'istanza senza collegarsi a un asset esterno o annidabile tramite script.

Il controllo gestore elastici indicherà se una configurazione è condivisa o inline come parte dell'istanza corrente visualizzando un messaggio nel controllo proprietà. Inoltre, le istanze condivise non saranno modificabili direttamente nella finestra delle proprietà del gestore elastici, ma l'asset a cui si collega deve essere modificato direttamente per evitare modifiche accidentali nelle configurazioni condivise.

Elastics Manager offre opzioni per gli oggetti di configurazione per i tipi di trasformazione seguenti, ognuno dei quali rappresentato da un oggetto [di configurazione elastica](#elastic-configuration-object):

- Elastico di traduzione
- Elastico di rotazione
- Scalabilità elastica

#### <a name="elastic-configuration-object"></a>Oggetto di configurazione elastica

Una configurazione elastica definisce le proprietà per un sistema differenziale dell'oscillatore armeno smorzato.
Le proprietà seguenti possono essere modificate, ma sono già disponibili con un set di valori predefiniti in MRTK:

- **Massa:** massa dell'elemento oscillatore simulato.
- **HandK:** costante della mano a molle.
- **EndK:** costante spring estremità finale.
- **SnapK:** costante di spring del punto di ancoraggio.
- **Trascinare**: fattore di trascinamento/smorzazione, proporzionale alla velocità.

### <a name="elastics-extents"></a>Extent elastici

Le impostazioni degli extent elastici variano a seconda del tipo di manipolazione. La traslazione e la scala sono rappresentate da [extent elastici del volume](#volume-elastic-extent) e la rotazione è rappresentata da un extent [elastico quaternione.](#quaternion-elastic-extent)

#### <a name="volume-elastic-extent"></a>Extent elastico del volume

Gli extent del volume definiscono uno spazio tridimensionale in cui è possibile spostare l'oscillatore armonico smorzato.

![Limiti elastici di estensione del volume](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds:** rappresenta i limiti inferiori dello spazio elastico.
- **UseBounds:** indica se i limiti di estensione devono essere rispettati dal sistema. Se true, quando l'iterazione corrente della posizione di destinazione non rientra nei limiti di estensione, verrà applicata la forza finale.
- **SnapPoints:** punti all'interno dello spazio a cui verrà allineato il sistema.
- **RepeatSnapPoints:** ripete i punti di ancoraggio all'infinito. I punti di allineamento esistenti fungeranno da modulo in cui i punti di allineamento effettivi vengono mappati ai multipli interi più vicini di ogni punto di allineamento.
- **SnapRadius:** distanza da cui i punti di ancoraggio iniziano a forzare la spring.

![Griglia di allineamento del volume elastico](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Extent elastico quaternione

Gli extent quaternione definiscono uno spazio di rotazione quattrodimensionale in cui l'oscillatore armonico smorzato è libero di ruotare.

![Esempio di rotazione elastica](../images/elastics/Elastics_Rotation.gif)

- **SnapPoints:** angoli euleri su cui verrà allineato il sistema.
- **RepeatSnapPoints:** ripete i punti di ancoraggio. I punti di allineamento esistenti fungeranno da modulo in cui i punti di allineamento effettivi vengono mappati ai multipli interi più vicini di ogni punto di allineamento.
- **SnapRadius:** angolo di arco in corrispondenza del quale i punti di allineamento iniziano forzando la spring in gradi euleri.

## <a name="elastics-example-scene"></a>Scena di esempio elastici

È possibile trovare esempi di configurazioni elastiche nella `ElasticSystemExample` scena.

![Scena di esempio di Elastics](../images/elastics/Elastics_Example_Scene.png)
