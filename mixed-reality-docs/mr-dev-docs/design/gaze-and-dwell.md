---
title: Sguardo fisso e attesa
description: Ottenere una panoramica generale del modello di input sguardo fisso e testa per applicazioni di realtà mista.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, sguardo, interazione, progettazione, tracciamento oculare, tracciamento della testa, visore per realtà mista, visore per realtà mista windows, visore per realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: c65c13b06df70ed5471b283ad349dd72e1575018a98913177983d7a13571d666
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213675"
---
# <a name="gaze-and-dwell"></a>Sguardo fisso e attesa

Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili.
I comandi vocali possono anche essere inaffidabili in determinati contesti, ad esempio in condizioni eccessivamente forti.
Gaze and dwell offre un meccanismo familiare e facile da usare per lavorare con testa in su e senza HoloLens.
Inoltre, lo sguardo e l'avarita sono un ottimo fallback, indipendente dalle interferenze acustiche o dai vincoli di silenzio nell'ambiente operativo.
Distinguiamo due varianti di sguardo e _sguardo:_ [sguardo](gaze-and-dwell-head.md) a testa e sguardo e sguardo [fisso e sguardo fisso.](gaze-and-dwell-eyes.md)

## <a name="scenarios"></a>Scenari

Lo sguardo fisso e l'ambiente sono molto importanti in scenari in cui le mani di una persona sono occupate da altre attività e la voce non è affidabile al 100% o disponibile a causa di vincoli ambientali o sociali.
Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile.
Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore.
L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso.
Lo sguardo e l'allarme consentono alla persona che usa HoloLens di esplorare in modo sicuro il materiale di riferimento senza interrompere il flusso di lavoro.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modello di input</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e attesa</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
    </tr>
     <tr>
        <td>Sguardo fisso e attesa</td>
        <td>❌ Non disponibile</td>
        <td>✔️ Consigliato</td>
        <td>❌ Non disponibile</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>Vedi anche

* [Interazione basata sullo sguardo](eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)