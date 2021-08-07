---
title: Movimento di avvio
description: Informazioni su come usare il movimento di avvio per richiamare il menu Start HoloLens e Windows Mixed Reality visori VR immersive.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realtà mista, movimenti, interazione, progettazione, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit, fiore
ms.openlocfilehash: f3ad9309c7232f20a25060b1d98d7374272ceea00f24be18d7263b8ec7002fb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213741"
---
# <a name="start-gesture"></a>Movimento di avvio

Il movimento Start è un movimento della mano usato per richiamare il menu Start. Equivale a premere il tasto Windows tastiera, il pulsante Xbox nei controller Xbox o il pulsante Windows nei controller del movimento immersive del visore VR. Prestare particolare attenzione ai movimenti di sistema riservati in ogni dispositivo di realtà mista per evitare conflitti durante la progettazione delle interazioni.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Fioritura</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Pulsante a mano</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Sguardo fisso e avvicinamento del palmo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Fioritura

"Bloom" è stato progettato per visualizzare il menu Start in HoloLens (prima generazione), che è un movimento simbolico che simula un fiore. È distintivo per un'interazione sicura, facile da usare e veloce da richiamare. Per usare il movimento, tieni la mano con il palmo in su e la punta del dito insieme, quindi apri la mano stendendo le dita.

:::row:::
    :::column:::
        ![Chiusura di Bloom](images/bloom-close.png)<br>
        **Passaggio 1: Palm up with fingertips together**<br>
    :::column-end:::
    :::column:::
        ![Bloom open](images/bloom-open.png)<br>
        **Passaggio 2: Palm up with fingertips spread**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Movimento di avvio

In HoloLens 2 è stato sostituito il movimento Bloom con un pulsante di tocco virtuale, più istintivo per gli utenti. Mostrando agli utenti il pulsante sul lente, possono contattare intuitivamente e premere il pulsante con l'altra mano.

:::row:::
    :::column:::
        ![Pulsante di sospensione pronto](images/wrist-button-ready.png)<br>
        **Passaggio 1: Palm up per visualizzare il pulsante di sospensione**<br>
    :::column-end:::
    :::column:::
        ![Pressione del pulsante a mano](images/wrist-button-press.png)<br>
        **Passaggio 2: Premere il pulsante di sospensione**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>Movimento Start con una mano

> [!IMPORTANT]
> Per il funzionamento del movimento Start con una sola mano:
>
> 1. È necessario eseguire l'aggiornamento all'aggiornamento di novembre 2019 (build 18363.1039) o versione successiva.
> 1. Gli occhi devono essere calibrati sul dispositivo in modo che il tracciamento oculare funzioni correttamente. Se non vengono visualizzati punti di ingrandimento intorno all'icona Start quando la si osserva, gli occhi non vengono calibrati sul dispositivo.

È anche possibile usare il movimento Start con una sola mano. Tieni la mano con il palmo rivolto verso di te e osserva **l'icona Start** sul tuo sguardo interno. **Tenendo sotto controllo l'icona**, avvicinare le dita del pollice e dell'indice.<br>
:::row:::
    :::column:::
        ![Pulsante di sospensione pronto](images/wrist-button-ready.png)<br>
        **Passaggio 1: Palm up per visualizzare il pulsante di sospensione**<br>
    :::column-end:::
    :::column:::
        ![Avvicinamento delle dita del pulsante a mano](images/wrist-button-pinch.png)<br>
        **Passaggio 2: Sguardo fisso sul pulsante e quindi avvicinamento delle dita**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Vedi anche

* [Interazioni istintive](interaction-fundamentals.md)
* [Sguardo fisso](eye-tracking.md)
* [Input vocale](voice-input.md)