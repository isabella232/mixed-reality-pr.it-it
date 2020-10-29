---
title: Sguardo e dimora
description: Panoramica generale del modello di input di tipo (occhio/testa)
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, abitazione, interazione, progettazione, rilevamento degli occhi, verifica della testa
ms.openlocfilehash: ee8b6487079a071fe84606949314f2dd315df45f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686980"
---
# <a name="gaze-and-dwell"></a>Sguardo e dimora

Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili.
I comandi vocali possono anche essere inaffidabili in determinati contesti, ad esempio in condizioni troppo potenti.
Sguardi e abitazioni offre un meccanismo familiare e facile da gestire per l'esecuzione di attività di Head-up e hands-free in HoloLens.
Inoltre, lo sguardo e l'abitazione sono un ottimo fallback indipendente dall'interferenza del rumore o dai vincoli di silenzio nell'ambiente operativo.
Si distinguono due varianti di _sguardo e dimora_ , ovvero lo [sguardo](gaze-and-dwell-head.md) e l'abitato e lo [sguardo e l'abitazione](gaze-and-dwell-eyes.md).

## <a name="scenarios"></a>Scenari

Lo sguardo e l'abitazione sono eccellenti negli scenari in cui le mani di una persona sono occupate da altre attività e la voce non è del 100% affidabile o disponibile a causa di vincoli ambientali o sociali.
Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile.
Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore.
L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso.
Lo sguardo e l'abitazione consentono all'utente che usa HoloLens di esplorare in modo sicuro il materiale di riferimento senza interrompere il flusso di lavoro.

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
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e attesa</td>
        <td>✔️ Consigliata</td>
        <td>✔️ Consigliata</td>
        <td>✔️ Consigliata</td>
    </tr>
     <tr>
        <td>Sguardo fisso e attesa</td>
        <td>❌ Non disponibile</td>
        <td>✔️ Consigliata</td>
        <td>❌ Non disponibile</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>Vedere anche
* [Interazione basata sullo sguardo](eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)
