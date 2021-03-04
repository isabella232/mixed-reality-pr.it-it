---
title: InputAnimationFileFormat
description: Documentazione sulla specifica del formato di file binario di animazione di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 5ec2b3f3ac83ee0ca1923cb62b36fe80edc22120
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782978"
---
# <a name="input-animation-binary-file-format-specification"></a>Specifica del formato file binario animazione input

## <a name="overall-structure"></a>Struttura complessiva

Il file binario di animazione di input inizia con un numero intero a 64 bit. Il valore di questo numero in notazione esadecimale è `0x6a8faf6e0f9e42c6` e può essere usato per identificare i file di animazione di input validi.

Gli otto byte successivi sono due valori Int32 che dichiarano il numero di versione principale e secondario del file.

Il resto del file viene occupato dai dati di animazione, che possono variare tra i numeri di versione.

| Sezione | Tipo |
|---------|------|
| Numero magico | Int64 |
| Numero di versione principale | Int32 |
| Numero di versione secondario | Int32 |
| Dati di animazione | _vedere la sezione Version_ |

## <a name="version-10"></a>Versione 1,0

I dati di animazione di input sono costituiti da una sequenza di curve di animazione. Il numero e il significato delle curve di animazione sono corretti, ma ogni curva può avere un numero diverso di fotogrammi chiave.

| Sezione | Tipo |
|---------|------|
| Fotocamera | [Pose curve](#pose-curves) |
| Mano rilevata a sinistra | [Curva booleana](#boolean-curve) |
| Rilevamento a destra della mano | [Curva booleana](#boolean-curve) |
| Mano pizzicata a sinistra | [Curva booleana](#boolean-curve) |
| Pizzica a destra | [Curva booleana](#boolean-curve) |
| Giunzioni a sinistra | [Curve di pose congiunte](#joint-pose-curves) |
| Giunzioni a destra | [Curve di pose congiunte](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>Curve di pose congiunte

Per ogni mano, viene archiviata una sequenza di curve di animazione congiunta. Il numero di giunzioni è fisso e viene archiviato un set di curve di pose per ogni giunzione.

| Sezione | Tipo |
|---------|------|
| nessuno | [Pose curve](#pose-curves) |
| Del polso | [Pose curve](#pose-curves) |
| Palm | [Pose curve](#pose-curves) |
| ThumbMetacarpalJoint | [Pose curve](#pose-curves) |
| ThumbProximalJoint | [Pose curve](#pose-curves) |
| ThumbDistalJoint | [Pose curve](#pose-curves) |
| ThumbTip | [Pose curve](#pose-curves) |
| IndexMetacarpal | [Pose curve](#pose-curves) |
| IndexKnuckle | [Pose curve](#pose-curves) |
| IndexMiddleJoint | [Pose curve](#pose-curves) |
| IndexDistalJoint | [Pose curve](#pose-curves) |
| IndexTip | [Pose curve](#pose-curves) |
| MiddleMetacarpal | [Pose curve](#pose-curves) |
| MiddleKnuckle | [Pose curve](#pose-curves) |
| MiddleMiddleJoint | [Pose curve](#pose-curves) |
| MiddleDistalJoint | [Pose curve](#pose-curves) |
| MiddleTip | [Pose curve](#pose-curves) |
| RingMetacarpal | [Pose curve](#pose-curves) |
| RingKnuckle | [Pose curve](#pose-curves) |
| RingMiddleJoint | [Pose curve](#pose-curves) |
| RingDistalJoint | [Pose curve](#pose-curves) |
| RingTip | [Pose curve](#pose-curves) |
| PinkyMetacarpal | [Pose curve](#pose-curves) |
| PinkyKnuckle | [Pose curve](#pose-curves) |
| PinkyMiddleJoint | [Pose curve](#pose-curves) |
| PinkyDistalJoint | [Pose curve](#pose-curves) |
| PinkyTip | [Pose curve](#pose-curves) |

### <a name="pose-curves"></a>Pose curve

Le curve pose sono una sequenza di 3 curve di animazione per il vettore di posizione, seguite da 4 curve di animazione per il quaternione di rotazione.

| Sezione | Tipo |
|---------|------|
| Posizione X | [Curva float](#float-curve) |
| Posizione Y | [Curva float](#float-curve) |
| Posizione Z | [Curva float](#float-curve) |
| Rotazione X | [Curva float](#float-curve) |
| Rotazione Y | [Curva float](#float-curve) |
| Rotazione Z | [Curva float](#float-curve) |
| Rotazione W | [Curva float](#float-curve) |

### <a name="float-curve"></a>Curva float

Le curve a virgola mobile sono le curve di Bézier completamente vere con un numero variabile di fotogrammi chiave. Ogni fotogramma chiave archivia un valore di ora e una curva, nonché tangenti e pesi sul lato sinistro e destro di ogni fotogramma chiave.

| Sezione | Tipo |
|---------|------|
| Modalità pre-wrapping | Int32, [modalità a capo automatico](#wrap-mode) |
| Modalità di post-wrapping | Int32, [modalità a capo automatico](#wrap-mode) |
| Numero di fotogrammi chiave | Int32 |
| KeyFrames | [Fotogramma chiave float](#float-keyframe) |

### <a name="float-keyframe"></a>Fotogramma chiave float

Un fotogramma chiave float archivia i valori della tangente e del peso insieme al valore e all'ora di base.

| Sezione | Tipo |
|---------|------|
| Tempo | Float32 |
| Valore | Float32 |
| Intangente | Float32 |
| Distangente | Float32 |
| Peso | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32, [modalità ponderata](#weighted-mode) |

### <a name="boolean-curve"></a>Curva booleana

Le curve booleane sono semplici sequenze di valori on/off. Su ogni fotogramma chiave, il valore della curva viene immediatamente invertito.

| Sezione | Tipo |
|---------|------|
| Modalità pre-wrapping | Int32, [modalità a capo automatico](#wrap-mode) |
| Modalità di post-wrapping | Int32, [modalità a capo automatico](#wrap-mode) |
| Numero di fotogrammi chiave | Int32 |
| KeyFrames | [Fotogramma chiave booleana](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>Fotogramma chiave booleana

Un fotogramma chiave booleano archivia solo un'ora e un valore.

| Sezione | Tipo |
|---------|------|
| Tempo | Float32 |
| Valore | Float32 |

### <a name="wrap-mode"></a>Modalità a capo automatico

La semantica delle modalità pre-e post-wrap segue la definizione di [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) . Si tratta di una combinazione dei bit seguenti:

| Valore | Significato |
|-------|---------|
| 0 | Impostazione predefinita: legge la modalità di ripetizione predefinita impostata su un valore superiore. |
| 1 | Una volta: quando il tempo raggiunge la fine del clip di animazione, il clip verrà interrotto automaticamente e l'ora verrà reimpostata all'inizio della clip. |
| 2 | Loop: quando il tempo raggiunge la fine del clip di animazione, l'ora continuerà all'inizio. |
| 4 | PingPong: quando il tempo raggiunge la fine della clip di animazione, l'ora eseguirà il ping di un posto tra l'inizio e la fine. |
| 8 | ClampForever: riproduce l'animazione. Quando raggiunge la fine, continuerà a riprodurre l'ultimo frame senza interrompere la riproduzione. |

### <a name="weighted-mode"></a>Modalità ponderata

La semantica della modalità ponderata segue la definizione di [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) .

| Valore | Significato |
|-------|---------|
| 0 | None: escludere sia il peso che il peso quando si calcolano i segmenti della curva. |
| 1 | In: includere il peso durante il calcolo del segmento della curva precedente. |
| 2 | Out: includere l'outgramma durante il calcolo del segmento di curva successivo. |
| 3 | Entrambi: includono il peso e il peso quando si calcolano i segmenti della curva. |
