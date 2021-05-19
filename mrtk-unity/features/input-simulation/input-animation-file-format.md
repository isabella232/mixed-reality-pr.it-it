---
title: Formato del file di animazione di input
description: Documentazione sulla specifica del formato di file binario dell'animazione di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ba232818c0a49d803ca6fae0b5adbc64e6deefa8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145127"
---
# <a name="input-animation-binary-file-format-specification"></a>Specifica del formato di file binario dell'animazione di input

## <a name="overall-structure"></a>Struttura complessiva

Il file binario dell'animazione di input inizia con un numero intero a 64 bit. Il valore di questo numero in notazione esadecimale è e può essere usato per identificare `0x6a8faf6e0f9e42c6` i file di animazione di input validi.

Gli otto byte successivi sono due valori Int32 che dichiarano il numero di versione principale e secondario del file.

Il resto del file viene utilizzato dai dati di animazione, che possono cambiare tra i numeri di versione.

| Sezione | Tipo |
|---------|------|
| Numero magico | Int64 |
| Numero di versione principale | Int32 |
| Numero di versione secondaria | Int32 |
| Dati di animazione | _vedere la sezione relativa alla versione_ |

## <a name="version-11"></a>Versione 1.1

I dati di animazione di input sono costituiti da tre valori booleani che indicano se l'animazione contiene dati Camera, Hand e Eye Gaze, seguiti da una sequenza di curve di animazione. Le curve presenti dipendono dai valori di questi valori booleani. Ogni curva può avere un numero diverso di fotogrammi chiave.

| Sezione | Type | Note |
|---------|------|------|
| Ha la posizione della fotocamera | Booleano | |
| Ha dati della mano | Booleano | |
| Ha lo sguardo fisso| Booleano | |
| Fotocamera | [Curve di posizione](#pose-curves) | Solo se La posizione della fotocamera è true |
| Mano tracciata a sinistra | [Curva booleana](#boolean-curve) | Solo se Has Hand Data è true |
| Mano tracciata a destra | [Curva booleana](#boolean-curve) | Solo se Has Hand Data è true |
| Avvicinamento della mano verso sinistra | [Curva booleana](#boolean-curve) | Solo se Has Hand Data è true |
| Avvicinamento delle dita a destra | [Curva booleana](#boolean-curve) | Solo se Has Hand Data è true |
| Giunzioni della mano a sinistra | [Curve di posizione giunzione](#joint-pose-curves) | Solo se Has Hand Data è true |
| Giunzioni della mano a destra | [Curve di posizione giunzione](#joint-pose-curves) | Solo se Has Hand Data è true |
| Sguardo fisso | [Curve di raggio](#ray-curves)] | Solo se Ha sguardo fisso è true |

## <a name="version-10"></a>Versione 1.0

I dati di animazione di input sono costituiti da una sequenza di curve di animazione. Il numero e il significato delle curve di animazione sono fissi, ma ogni curva può avere un numero diverso di fotogrammi chiave.

| Sezione | Tipo |
|---------|------|
| Fotocamera | [Curve di posizione](#pose-curves) |
| Mano tracciata a sinistra | [Curva booleana](#boolean-curve) |
| Mano tracciata a destra | [Curva booleana](#boolean-curve) |
| Avvicinamento della mano verso sinistra | [Curva booleana](#boolean-curve) |
| Avvicinamento delle dita a destra | [Curva booleana](#boolean-curve) |
| Giunzioni della mano a sinistra | [Curve di posizione giunzione](#joint-pose-curves) |
| Giunzioni della mano a destra | [Curve di posizione giunzione](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>Curve di posizione giunzione

Per ogni mano viene archiviata una sequenza di curve di animazione congiunte. Il numero di giunzioni è fisso e viene archiviato un set di curve di posizione per ogni giunzione.

| Sezione | Tipo |
|---------|------|
| Nessuno | [Curve di posizione](#pose-curves) |
| Polso | [Curve di posizione](#pose-curves) |
| Palm | [Curve di posizione](#pose-curves) |
| ThumbMetacarpalJoint | [Curve di posizione](#pose-curves) |
| ThumbProximalJoint | [Curve di posizione](#pose-curves) |
| ThumbDistalJoint | [Curve di posizione](#pose-curves) |
| Descrizione comando | [Curve di posizione](#pose-curves) |
| IndexMetacarpal | [Curve di posizione](#pose-curves) |
| IndexKnuckle | [Curve di posizione](#pose-curves) |
| IndexMiddleJoint | [Curve di posizione](#pose-curves) |
| IndexDistalJoint | [Curve di pose](#pose-curves) |
| Suggerimento indice | [Curve di pose](#pose-curves) |
| MiddleMetacarpal | [Curve di pose](#pose-curves) |
| MiddleKnuckle | [Curve di pose](#pose-curves) |
| MiddleMiddleJoint | [Curve di pose](#pose-curves) |
| MiddleDistalJoint | [Curve di pose](#pose-curves) |
| Suggerimento intermedio | [Curve di pose](#pose-curves) |
| RingMetacarpal | [Curve di pose](#pose-curves) |
| RingKnuckle | [Curve di pose](#pose-curves) |
| RingMiddleJoint | [Curve di pose](#pose-curves) |
| RingDistalJoint | [Curve di pose](#pose-curves) |
| Descrizione comando | [Curve di pose](#pose-curves) |
| PinkyMetacarpal | [Curve di pose](#pose-curves) |
| PinkyKnuckle | [Curve di pose](#pose-curves) |
| PinkyMiddleJoint | [Curve di pose](#pose-curves) |
| PinkyDistalJoint | [Curve di pose](#pose-curves) |
| PinkyTip | [Curve di pose](#pose-curves) |

### <a name="pose-curves"></a>Curve di posizione

Le curve di posizione sono una sequenza di 3 curve di animazione per il vettore di posizione, seguite da 4 curve di animazione per il quaternione di rotazione.

| Sezione | Tipo |
|---------|------|
| Posizione X | [Curva float](#float-curve) |
| Posizione Y | [Curva float](#float-curve) |
| Posizione Z | [Float Curve](#float-curve) |
| Rotazione X | [Float Curve](#float-curve) |
| Rotazione Y | [Float Curve](#float-curve) |
| Rotazione Z | [Float Curve](#float-curve) |
| Rotazione W | [Float Curve](#float-curve) |

### <a name="ray-curves"></a>Curve di raggio

Le curve di raggio sono una sequenza di 3 curve di animazione per il vettore di origine, seguite da 3 curve di animazione per il vettore di direzione.

| Sezione | Tipo |
|---------|------|
| Origine X | [Float Curve](#float-curve) |
| Origine Y | [Float Curve](#float-curve) |
| Origine Z | [Float Curve](#float-curve) |
| Direzione X | [Float Curve](#float-curve) |
| Direzione Y | [Curva float](#float-curve) |
| Direzione Z | [Curva float](#float-curve) |

### <a name="float-curve"></a>Curva float

Le curve a virgola mobile sono curve Bézier completamente funzionanti con un numero variabile di fotogrammi chiave. Ogni fotogramma chiave archivia un tempo e un valore di curva, nonché tangenti e pesi sul lato sinistro e destro di ogni fotogramma chiave.

| Sezione | Tipo |
|---------|------|
| Modalità di pre-ritorno a capo | Int32, [modalità di ritorno a capo](#wrap-mode) |
| Modalità post-wrapping | Int32, [modalità di ritorno a capo](#wrap-mode) |
| Numero di fotogrammi chiave | Int32 |
| Fotogrammi chiave | [Fotogramma chiave float](#float-keyframe) |

### <a name="float-keyframe"></a>Fotogramma chiave float

Un fotogramma chiave float archivia i valori di tangente e peso insieme all'ora e al valore di base.

| Sezione | Tipo |
|---------|------|
| Ora | Float32 |
| valore | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32, [modalità ponderata](#weighted-mode) |

### <a name="boolean-curve"></a>Curva booleana

Le curve booleane sono semplici sequenze di valori on/off. In ogni fotogramma chiave il valore della curva viene capovolto immediatamente.

| Sezione | Tipo |
|---------|------|
| Modalità di pre-wrapping | Int32, [modalità wrap](#wrap-mode) |
| Modalità post-wrapping | Int32, [modalità wrap](#wrap-mode) |
| Numero di fotogrammi chiave | Int32 |
| Fotogrammi chiave | [Fotogramma chiave booleano](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>Fotogramma chiave booleano

Un fotogramma chiave booleano archivia solo un'ora e un valore.

| Sezione | Tipo |
|---------|------|
| Ora | Float32 |
| valore | Float32 |

### <a name="wrap-mode"></a>Modalità di ritorno a capo

La semantica delle modalità Pre e Post-Wrap segue la [definizione WrapMode di Unity.](https://docs.unity3d.com/ScriptReference/WrapMode.html) Sono una combinazione dei bit seguenti:

| valore | Significato |
|-------|---------|
| 0 | Impostazione predefinita: legge la modalità di ripetizione predefinita impostata più in alto. |
| 1 | Una volta: quando il tempo raggiunge la fine del clip di animazione, la riproduzione del clip viene interrotta automaticamente e l'ora viene reimpostata all'inizio del clip. |
| 2 | Ciclo: quando il tempo raggiunge la fine del clip di animazione, il tempo continuerà all'inizio. |
| 4 | PingPong: quando il tempo raggiunge la fine del clip di animazione, il tempo esegue il ping pong tra l'inizio e la fine. |
| 8 | ClampForever: riproduce l'animazione. Quando raggiunge la fine, continuerà a riprodurre l'ultimo fotogramma e non smetterà mai di riprodurre. |

### <a name="weighted-mode"></a>Modalità ponderata

La semantica della modalità Ponderata segue la [definizione di Unity WeightedMode.](https://docs.unity3d.com/ScriptReference/WeightedMode.html)

| valore | Significato |
|-------|---------|
| 0 | Nessuno: esclude sia inWeight che outWeight durante il calcolo dei segmenti della curva. |
| 1 | In: Includere inWeight durante il calcolo del segmento della curva precedente. |
| 2 | Out: includere outWeight durante il calcolo del segmento di curva successivo. |
| 3 | Entrambi: includere inWeight e outWeight durante il calcolo dei segmenti della curva. |
