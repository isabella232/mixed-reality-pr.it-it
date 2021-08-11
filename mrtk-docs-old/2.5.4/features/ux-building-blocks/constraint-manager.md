---
title: ConstraintManager
description: Panoramica di Gestione vincoli in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 96802feffcfe1c238c1a6c7022166a68ae593add744ee6d102b95337ef1421c3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198591"
---
# <a name="constraint-manager"></a>Gestione vincoli

Gestione vincoli consente di applicare un set di componenti di vincolo a una trasformazione. È possibile prendere in considerazione i componenti di tipo associati [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) all'oggetto di gioco.
Per impostazione predefinita, Gestione vincoli raccoglierà automaticamente tutti [i componenti](#transform-constraints) dei vincoli collegati all'oggetto gioco e li applicherà alle trasformazioni elaborate.
Tuttavia, gli utenti possono scegliere di configurare manualmente l'elenco di vincoli applicati e di applicare solo un subset di vincoli associati.

Attualmente gli elementi dell'esperienza utente MRTK seguenti supportano la gestione vincoli:

- [Controllo Limiti](bounds-control.md)
- [Manipolatore di oggetti](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>Proprietà e campi del controllo

Gestione vincoli può essere gestito in due modalità:

- Selezione automatica dei vincoli
- Selezione manuale dei vincoli

### <a name="auto-constraint-selection"></a>Selezione automatica dei vincoli

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

La modalità predefinita di gestione vincoli, la selezione automatica dei [vincoli,](#add-constraint-to-game-object) [](#go-to-component) fornirà un elenco di tutti i componenti del vincolo associato, oltre a passare ai pulsanti e un pulsante Aggiungi vincolo .

#### <a name="add-constraint-to-game-object"></a>Aggiungere un vincolo all'oggetto gioco

Questo pulsante consente di aggiungere un componente vincolo direttamente dal controllo di Gestione vincoli. Tutti i tipi di vincolo in un progetto devono essere visibili qui. Per [altre informazioni, vedere](#transform-constraints) Vincoli di trasformazione.

#### <a name="go-to-component"></a>Vai al componente

Tutti i vincoli trovati nell'oggetto verranno elencati qui con *un pulsante Vai al componente.* Questo pulsante farà scorrere il controllo fino al componente vincolo selezionato in modo che possa essere configurato.

### <a name="manual-constraint-selection"></a>Selezione manuale dei vincoli

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

Se Gestione vincoli è impostato sulla modalità manuale, solo i vincoli collegati nell'elenco di vincoli vengono elaborati e applicati alla trasformazione. L'elenco visualizzato mostrerà solo i vincoli selezionati dall'utente, nonché [i](#go-to-component) pulsanti o le opzioni per rimuovere o aggiungere voci.
Quando si abilita la modalità manuale per la prima volta, Gestione vincoli popola l'elenco per tutti i componenti disponibili come punto di partenza per la selezione dei componenti dei vincoli associati.

### <a name="remove-entry"></a>Rimuovi voce

La voce verrà rimossa dall'elenco selezionato manualmente. Si noti che questa opzione non rimuove il componente vincolo dall'oggetto del gioco. I componenti di vincolo devono sempre essere rimossi manualmente per garantire che non vengano accidentalmente infrante eventuali altri componenti che fanno riferimento a questo componente.

### <a name="add-entry"></a>Aggiungere una voce

Aggiungi voce aprirà un elenco a discesa che mostra tutti i componenti dei vincoli disponibili che non sono ancora presenti nell'elenco manuale. Facendo clic su una delle voci che il componente verrà aggiunto alla selezione manuale del vincolo.

### <a name="add-new-constraint"></a>Aggiungere un nuovo vincolo

Questa opzione aggiungerà un componente del tipo selezionato all'oggetto gioco e aggiungerà il componente vincolo appena creato all'elenco di vincoli manuale.

## <a name="transform-constraints"></a>Vincoli di trasformazione

I vincoli possono essere usati per limitare la manipolazione in qualche modo. Ad esempio, alcune applicazioni possono richiedere la rotazione, ma anche che l'oggetto rimanga in posizione verticale. In questo caso, è possibile aggiungere un oggetto all'oggetto e usare per limitare la `RotationAxisConstraint` rotazione alla rotazione dell'asse Y. MRTK fornisce una serie di vincoli, tutti descritti di seguito.

È anche possibile definire nuovi vincoli e usarli per creare un comportamento di manipolazione univoco che potrebbe essere necessario per alcune applicazioni. A tale scopo, creare uno script che eredita da e [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) implementare la proprietà astratta `ConstraintType` e il metodo `ApplyConstraint` astratto. Quando si aggiunge un nuovo vincolo all'oggetto, deve vincolare la manipolazione nel modo definito. Questo nuovo vincolo deve essere visualizzato anche nella selezione automatica di [Gestione](#auto-constraint-selection) vincoli o nell'elenco [a](#add-entry) discesa Aggiungi voce in modalità manuale.

Tutti i vincoli forniti da MRTK condividono le proprietà seguenti:

#### <a name="hand-type"></a>Tipo di mano

Specifica se il vincolo viene usato per una mano, due mani o per entrambi i tipi di manipolazione. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Una mano:* il vincolo verrà usato durante la manipolazione con una mano, se selezionato.
- *A due mani:* il vincolo verrà usato durante la manipolazione a due mani, se selezionato.

#### <a name="proximity-type"></a>Tipo di prossimità

Specifica se il vincolo viene usato per la manipolazione vicina, lontana o per entrambi i tipi. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Vicino:* il vincolo verrà usato durante la manipolazione vicina, se selezionato.
- *Far:* il vincolo verrà usato durante la manipolazione da lontano, se selezionato.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

Quando questo vincolo è associato a un oggetto, la rotazione sarà limitata in modo che l'oggetto si faccia sempre fronte all'utente. Ciò è utile per gli ardesia o i pannelli. Le proprietà per `FaceUserConstraint` sono le seguenti:

#### <a name="face-away"></a>Viso lontano

L'oggetto si allontana dall'utente se è true.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

Questo vincolo corregge la distanza tra l'oggetto modificato e un'altra trasformazione di oggetto all'inizio della manipolazione. Ciò è utile per comportamenti come la correzione della distanza tra l'oggetto modificato e la trasformazione della testa. Le proprietà per `FixedDistanceConstraint` sono le seguenti:

#### <a name="constraint-transform"></a>Trasformazione dei vincoli

Questa è l'altra trasformazione a cui l'oggetto modificato avrà una distanza fissa. Il valore predefinito è la trasformazione della fotocamera.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

Questo vincolo corregge la rotazione relativa tra l'utente e l'oggetto modificato durante la modifica. Ciò è utile per gli ardeggiamenti o i pannelli in quanto garantisce che l'oggetto modificato abbia sempre lo stesso viso dell'utente all'inizio della manipolazione. `FixedRotationToUserConstraint`l'oggetto non dispone di proprietà univoche.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

Questo vincolo corregge la rotazione globale dell'oggetto modificato durante la modifica. Questa operazione può essere utile nei casi in cui nessuna rotazione deve essere disodepolata dalla manipolazione. `FixedRotationToWorldConstraint`l'oggetto non ha proprietà univoche:

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

Quando questo vincolo è associato a un oggetto, indipendentemente dalla distanza dell'oggetto dall'utente, manterrà le stesse dimensioni apparenti per l'utente(ad esempio, l'oggetto avrà la stessa proporzione del campo di visualizzazione dell'utente). Può essere usato per garantire che uno slate o un pannello di testo rimanga leggibile durante la modifica. `MaintainApparentSizeConstraint`l'oggetto non ha proprietà univoche:

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

Questo vincolo può essere usato per correggere gli assi lungo i quali è possibile spostare un oggetto modificato. Può essere utile per modificare gli oggetti sulla superficie di un piano o lungo una linea. Le proprietà per `MoveAxisConstraint` sono le seguenti:

#### <a name="constraint-on-movement"></a>Vincolo sullo spostamento

Specifica gli assi su cui impedire lo spostamento. Per impostazione predefinita, questi assi saranno globali anziché locali, ma possono essere modificati di seguito. Poiché questa proprietà è un flag, è possibile selezionare un numero qualsiasi di opzioni.

- *Asse X:* lo spostamento lungo l'asse x è vincolato se selezionato.
- *Asse Y:* lo spostamento lungo l'asse y è vincolato se selezionato.
- *Asse Z:* lo spostamento lungo l'asse z è vincolato se selezionato.

#### <a name="use-local-space-for-constraint"></a>Usare lo spazio locale per il vincolo

Vincola gli assi di trasformazione locali dell'oggetto modificato se true. False per impostazione predefinita.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

Questo vincolo può essere usato per correggere gli assi su cui può essere ruotato un oggetto modificato. Ciò può essere utile per mantenere un oggetto modificato in posizione verticale, ma consentendo comunque le rotazioni dell'asse y, ad esempio. Le proprietà per `RotationAxisConstraint` sono le seguenti:

#### <a name="constraint-on-rotation"></a>Vincolo alla rotazione

Specifica gli assi su cui impedire la rotazione. Per impostazione predefinita, questi assi saranno globali anziché locali, ma possono essere modificati di seguito. Poiché questa proprietà è un flag, è possibile selezionare un numero qualsiasi di opzioni.

- *Asse Y:* la rotazione intorno all'asse y è vincolata se selezionata.
- *Asse Z:* la rotazione intorno all'asse z è vincolata se selezionata.
- *Asse X:* la rotazione intorno all'asse x è vincolata se selezionata.

#### <a name="use-local-space-for-constraint"></a>Usare lo spazio locale per il vincolo

Vincola gli assi di trasformazione locali dell'oggetto modificato se true. False per impostazione predefinita.

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

Questo vincolo consente di impostare i valori minimo e massimo per la scala dell'oggetto modificato. Ciò è utile per impedire agli utenti di ridimensionare un oggetto troppo piccolo o troppo grande. Le proprietà per `MinMaxScaleConstraint` sono le seguenti:

#### <a name="scale-minimum"></a>Scalabilità minima

Valore di scala minimo durante la manipolazione.

#### <a name="scale-maximum"></a>Scalabilità massima

Valore di scala massima durante la manipolazione.

#### <a name="relative-to-initial-state"></a>Rispetto allo stato iniziale

Se true, i valori precedenti verranno interpretati come relativi alla scala iniziale degli oggetti. In caso contrario, verranno interpretati come valori di scala assoluti.
