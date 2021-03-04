---
title: ConstraintManager
description: Panoramica su Gestione vincoli in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7c1f32eb294fe32dd68df88521883bda1d1a1717
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781877"
---
# <a name="constraint-manager"></a>Gestione vincoli

Gestione vincoli consente di applicare un set di componenti dei vincoli a una trasformazione. I componenti di tipo [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) collegati all'oggetto gioco possono essere presi in considerazione.
Per impostazione predefinita, gestione vincoli raccoglie automaticamente tutti i [componenti dei vincoli](#transform-constraints) collegati all'oggetto gioco e li applica alle trasformazioni elaborate.
Tuttavia, gli utenti possono scegliere di configurare manualmente l'elenco dei vincoli applicati e consentire l'applicazione solo di un subset di vincoli collegati.

Attualmente gli elementi UX MRTK seguenti supportano Gestione vincoli:

- [Controllo dei limiti](BoundsControl.md)
- [Manipolatore di oggetti](ObjectManipulator.md)

## <a name="inspector-properties-and-fields"></a>Proprietà e campi di Inspector

Gestione vincoli può essere utilizzato in due modalità:

- Selezione vincolo automatico
- Selezione vincolo manuale

### <a name="auto-constraint-selection"></a>Selezione vincolo automatico

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection Properties">

La modalità predefinita di gestione vincoli, selezione vincolo automatica, fornirà un elenco di tutti i componenti dei vincoli collegati, nonché i [pulsanti Vai a](#go-to-component) e [Aggiungi vincolo](#add-constraint-to-game-object).

#### <a name="add-constraint-to-game-object"></a>Aggiungi vincolo all'oggetto gioco

Questo pulsante consente di aggiungere un componente vincolo direttamente dal controllo Gestione vincoli. Tutti i tipi di vincolo in un progetto devono essere visibili qui. Per altre informazioni, vedere [vincoli Transform](#transform-constraints) .

#### <a name="go-to-component"></a>Vai al componente

Tutti i vincoli trovati nell'oggetto verranno elencati qui con un pulsante *Vai al componente* . Questo pulsante farà sì che il controllo scorra fino al componente del vincolo selezionato, in modo che possa essere configurato.

### <a name="manual-constraint-selection"></a>Selezione vincolo manuale

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Constraint selection">

Se Gestione vincoli è impostato sulla modalità manuale, solo i vincoli collegati nell'elenco di vincoli vengono elaborati e applicati alla trasformazione. L'elenco visualizzato mostrerà solo i vincoli selezionati dall'utente, nonché i [pulsanti](#go-to-component) o le opzioni per rimuovere o aggiungere voci.
Quando si Abilita la modalità manuale per la prima volta, gestione vincoli compilerà l'elenco tutti i componenti disponibili come punto di partenza per la selezione dei componenti dei vincoli collegati.

### <a name="remove-entry"></a>Rimuovi voce

Questa operazione consente di rimuovere la voce dall'elenco selezionato manualmente. Si noti che questa opzione non rimuoverà il componente vincolo dall'oggetto Game. I componenti dei vincoli devono sempre essere rimossi manualmente per evitare di inavvertire eventuali altri componenti che fanno riferimento a questo componente.

### <a name="add-entry"></a>Aggiungi voce

Aggiungi voce verrà aperto un elenco a discesa che Mostra tutti i componenti dei vincoli disponibili che non sono ancora presenti nell'elenco manuale. Facendo clic su una delle voci, il componente verrà aggiunto alla selezione dei vincoli manuale.

### <a name="add-new-constraint"></a>Aggiungi nuovo vincolo

Questa opzione consente di aggiungere un componente del tipo selezionato all'oggetto gioco e aggiungere il componente vincolo appena creato all'elenco di vincoli manuale.

## <a name="transform-constraints"></a>Vincoli di trasformazione

I vincoli possono essere usati per limitare la manipolazione in qualche modo. Ad esempio, alcune applicazioni possono richiedere la rotazione, ma richiedono anche che l'oggetto rimanga verticale. In questo caso, `RotationAxisConstraint` è possibile aggiungere un oggetto all'oggetto e usarlo per limitare la rotazione alla rotazione dell'asse y. MRTK fornisce una serie di vincoli, tutti descritti di seguito.

È anche possibile definire nuovi vincoli e usarli per creare un comportamento di manipolazione univoco che potrebbe essere necessario per alcune applicazioni. A tale scopo, creare uno script che erediti da [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) e implementi la `ConstraintType` proprietà abstract e il `ApplyConstraint` metodo abstract. Quando si aggiunge un nuovo vincolo all'oggetto, è necessario vincolare la manipolazione nel modo in cui è stato definito. Questo nuovo vincolo dovrebbe inoltre essere visualizzato nell'elenco a discesa [selezione automatica](#auto-constraint-selection) gestione vincoli o [Aggiungi voce](#add-entry) in modalità manuale.

Tutti i vincoli forniti da MRTK condividono le proprietà seguenti:

#### <a name="hand-type"></a>Tipo di mano

Specifica se il vincolo viene utilizzato per una sola mano, due o entrambi i tipi di manipolazione. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Una sola mano*: il vincolo verrà usato durante una manipolazione gestita, se selezionato.
- *Due passate*: il vincolo verrà usato durante due manipolazioni gestite, se selezionato.

#### <a name="proximity-type"></a>Tipo di prossimità

Specifica se il vincolo viene utilizzato per i tipi di manipolazione near, di gran lunga o entrambi. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Near*: il vincolo verrà usato in prossimità della manipolazione, se selezionato.
- *Lontano*: il vincolo verrà usato durante la manipolazione di gran lunga se selezionato.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../Images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="face user constraint">

Quando questo vincolo è associato a un oggetto, la rotazione sarà limitata in modo che l'oggetto faccia sempre fronte all'utente. Questa operazione è utile per gli slate o i pannelli. Le proprietà per `FaceUserConstraint` sono le seguenti:

#### <a name="face-away"></a>Faccia fuori

L'oggetto viene rivolto dall'utente se true.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../Images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Face away">

Questo vincolo corregge la distanza tra l'oggetto modificato e un'altra trasformazione dell'oggetto all'avvio della manipolazione. Questa operazione è utile per comportamenti come la correzione della distanza dall'oggetto modificato alla trasformazione Head. Le proprietà per `FixedDistanceConstraint` sono le seguenti:

#### <a name="constraint-transform"></a>Trasformazione vincolo

Si tratta dell'altra trasformazione a cui l'oggetto modificato avrà una distanza fissa. Il valore predefinito è la trasformazione della fotocamera.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../Images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Distance Constraint">

Questo vincolo corregge la rotazione relativa tra l'utente e l'oggetto modificato durante la manipolazione. Questa operazione è utile per gli slate o i pannelli, in quanto assicura che l'oggetto modificato mostri sempre lo stesso aspetto all'utente, così come è stato fatto all'inizio della manipolazione. Non `FixedRotationToUserConstraint` dispone di proprietà univoche.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../Images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed Rotation to user">

Questo vincolo corregge la rotazione globale dell'oggetto modificato durante la manipolazione. Questa operazione può essere utile nei casi in cui non è necessario che la rotazione venga ripartita dalla manipolazione. Non `FixedRotationToWorldConstraint` dispone di proprietà univoche:

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../Images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Apparent size constraint">

Quando questo vincolo è associato a un oggetto, indipendentemente dalla distanza dell'oggetto dall'utente, manterrà le stesse dimensioni apparenti per l'utente (ad esempio, prenderà la stessa proporzione del campo di visualizzazione dell'utente). Questa operazione può essere utilizzata per garantire che uno Slate o un pannello di testo rimanga leggibile durante la manipolazione. Non `MaintainApparentSizeConstraint` dispone di proprietà univoche:

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../Images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Move Axis Constraint">

Questo vincolo può essere usato per correggere gli assi che possono essere spostati in un oggetto modificato. Questa operazione può essere utile per la modifica degli oggetti sulla superficie di un piano o lungo una linea. Le proprietà per `MoveAxisConstraint` sono le seguenti:

#### <a name="constraint-on-movement"></a>Vincolo durante lo spostamento

Specifica gli assi su cui impedire lo spostamento. Per impostazione predefinita, questi assi saranno globali anziché locali, ma è possibile modificarli sotto. Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.

- *Asse x*: se selezionato, lo spostamento lungo l'asse x è vincolato.
- *Asse y*: se selezionato, lo spostamento lungo l'asse y è vincolato.
- *Asse z*: lo spostamento lungo l'asse z è vincolato se selezionato.

#### <a name="use-local-space-for-constraint"></a>Usa spazio locale per il vincolo

Vincola gli assi di trasformazione locali dell'oggetto modificato se true. False per impostazione predefinita.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../Images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Rotation Axis Constraint">

Questo vincolo può essere usato per correggere gli assi che possono essere ruotati da un oggetto modificato. Questa operazione può essere utile per mantenere un oggetto manipolato verticalmente, ma che consente comunque di ruotare gli assi y, ad esempio. Le proprietà per `RotationAxisConstraint` sono le seguenti:

#### <a name="constraint-on-rotation"></a>Vincolo alla rotazione

Specifica gli assi per i quali impedire la rotazione. Per impostazione predefinita, questi assi saranno globali anziché locali, ma è possibile modificarli sotto. Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.

- *Asse y*: la rotazione sull'asse y è vincolata se selezionata.
- *Asse z*: la rotazione sull'asse z è vincolata se selezionata.
- *Asse x*: la rotazione sull'asse x è vincolata se selezionata.

#### <a name="use-local-space-for-constraint"></a>Usa spazio locale per il vincolo

Vincola gli assi di trasformazione locali dell'oggetto modificato se true. False per impostazione predefinita.

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../Images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="MinMax Scale constraint">

Questo vincolo consente di impostare i valori minimo e massimo per la scala dell'oggetto modificato. Questa operazione è utile per impedire agli utenti di ridimensionare un oggetto troppo piccolo o troppo grande. Le proprietà per `MinMaxScaleConstraint` sono le seguenti:

#### <a name="scale-minimum"></a>Dimensioni minime

Valore di scala minimo durante la manipolazione.

#### <a name="scale-maximum"></a>Scalabilità massima

Valore di scala massimo durante la manipolazione.

#### <a name="relative-to-initial-state"></a>Relativo allo stato iniziale

Se true, i valori precedenti verranno interpretati come relativi alla scala iniziale degli oggetti. In caso contrario, verranno interpretati come valori di scala assoluti.
