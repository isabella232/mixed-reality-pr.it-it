---
title: Formato del file di animazione di input
description: Documentazione sulla specifica del formato di file binario dell'animazione di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: bf77d976c9c894e6cf455a3a6b0e0c538912af2a9e8f8e2c7e847ba6e4657140
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222763"
---
# <a name="input-animation-file-format"></a>Formato del file di animazione di input

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
| Ha la posizione della fotocamera | Boolean | |
| Ha dati della mano | Boolean | |
| Ha lo sguardo fisso| Boolean | |
| Fotocamera | [Curve di pose](#pose-curves) | Solo se La posizione della fotocamera è true |
| Tracciato a mano a sinistra | [Curva booleana](#boolean-curve) | Solo se Has Hand Data è true |
| Tracciato a destra | [Curva booleana](#boolean-curve) | Solo se Has Hand Data è true |
| Avvicinamento delle dita a sinistra | [Curva booleana](#boolean-curve) | Solo se Has Hand Data è true |
| Avvicinamento delle dita a destra | [Curva booleana](#boolean-curve) | Solo se Has Hand Data è true |
| Giunzioni della mano a sinistra | [Curve di posizione congiunta](#joint-pose-curves) | Solo se Has Hand Data è true |
| Giunzioni della mano a destra | [Curve di posizione congiunta](#joint-pose-curves) | Solo se Has Hand Data è true |
| Sguardo fisso | [Curve di raggio](#ray-curves)] | Solo se ha lo sguardo fisso è true |

## <a name="version-10"></a>Versione 1.0

I dati di animazione di input sono costituiti da una sequenza di curve di animazione. Il numero e il significato delle curve di animazione sono fissi, ma ogni curva può avere un numero diverso di fotogrammi chiave.

| Sezione | Tipo |
|---------|------|
| Fotocamera | [Curve di pose](#pose-curves) |
| Tracciato a mano a sinistra | [Curva booleana](#boolean-curve) |
| Tracciato a destra | [Curva booleana](#boolean-curve) |
| Avvicinamento delle dita a sinistra | [Curva booleana](#boolean-curve) |
| Avvicinamento delle dita a destra | [Curva booleana](#boolean-curve) |
| Giunzioni della mano a sinistra | [Curve di posizione congiunta](#joint-pose-curves) |
| Giunzioni della mano a destra | [Curve di posizione congiunta](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>Curve di posizione congiunta

Per ogni mano viene archiviata una sequenza di curve di animazione articolare. Il numero di giunzioni è fisso e un set di curve di posizione viene archiviato per ogni giunzione.

| Sezione | Tipo |
|---------|------|
| Nessuno | [Curve di pose](#pose-curves) |
| Polso | [Curve di pose](#pose-curves) |
| Palm | [Curve di pose](#pose-curves) |
| ThumbMetacarpalJoint | [Curve di pose](#pose-curves) |
| ThumbProximalJoint | [Curve di pose](#pose-curves) |
| ThumbDistalJoint | [Curve di pose](#pose-curves) |
| Descrizione comando | [Curve di pose](#pose-curves) |
| IndexMetacarpal | [Curve di pose](#pose-curves) |
| IndexKnuckle | [Curve di pose](#pose-curves) |
| IndexMiddleJoint | [Curve di pose](#pose-curves) |
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
| Posizione Z | [Curva float](#float-curve) |
| Rotazione X | [Curva float](#float-curve) |
| Rotazione Y | [Curva float](#float-curve) |
| Rotazione Z | [Curva float](#float-curve) |
| Rotazione W | [Curva float](#float-curve) |

### <a name="ray-curves"></a>Curve a raggi

Le curve di raggio sono una sequenza di 3 curve di animazione per il vettore di origine, seguite da 3 curve di animazione per il vettore di direzione.

| Sezione | Tipo |
|---------|------|
| Origine X | [Curva float](#float-curve) |
| Origine Y | [Curva float](#float-curve) |
| Origine Z | [Curva float](#float-curve) |
| Direzione X | [Curva float](#float-curve) |
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
| Valore | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32, [modalità ponderata](#weighted-mode) |

### <a name="boolean-curve"></a>Curva booleana

Le curve booleane sono semplici sequenze di valori di on/off. In ogni fotogramma chiave il valore della curva viene capovolto immediatamente.

| Sezione | Tipo |
|---------|------|
| Modalità di pre-ritorno a capo | Int32, [modalità di ritorno a capo](#wrap-mode) |
| Modalità post-wrapping | Int32, [modalità di ritorno a capo](#wrap-mode) |
| Numero di fotogrammi chiave | Int32 |
| Fotogrammi chiave | [Fotogramma chiave booleano](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>Fotogramma chiave booleano

Un fotogramma chiave booleano archivia solo un'ora e un valore.

| Sezione | Tipo |
|---------|------|
| Ora | Float32 |
| Valore | Float32 |

### <a name="wrap-mode"></a>Modalità di ritorno a capo

La semantica delle modalità Pre e Post-Wrap segue la [definizione WrapMode di Unity.](https://docs.unity3d.com/ScriptReference/WrapMode.html) Sono una combinazione dei bit seguenti:

| Valore | Significato |
|-------|---------|
| 0 | Impostazione predefinita: legge la modalità di ripetizione predefinita impostata più in alto. |
| 1 | Una volta: quando il tempo raggiunge la fine del clip di animazione, la riproduzione del clip viene interrotta automaticamente e l'ora viene reimpostata all'inizio del clip. |
| 2 | Ciclo: quando il tempo raggiunge la fine del clip di animazione, il tempo continuerà all'inizio. |
| 4 | PingPong: quando il tempo raggiunge la fine del clip di animazione, il tempo esegue il ping pong tra l'inizio e la fine. |
| 8 | ClampForever: riproduce l'animazione. Quando raggiunge la fine, continuerà a riprodurre l'ultimo fotogramma e non smetterà mai di riprodurre. |

### <a name="weighted-mode"></a>Modalità ponderata

La semantica della modalità Ponderata segue la [definizione di Unity WeightedMode.](https://docs.unity3d.com/ScriptReference/WeightedMode.html)

| Valore | Significato |
|-------|---------|
| 0 | Nessuno: esclude sia inWeight che outWeight durante il calcolo dei segmenti della curva. |
| 1 | In: Includere inWeight durante il calcolo del segmento della curva precedente. |
| 2 | Out: includere outWeight durante il calcolo del segmento di curva successivo. |
| 3 | Entrambi: includere inWeight e outWeight durante il calcolo dei segmenti della curva. |
