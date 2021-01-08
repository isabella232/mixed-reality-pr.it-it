---
title: Azione di avvio
description: Informazioni su come usare il gesto di avvio per chiamare il menu Start in HoloLens e gli auricolari immersivi con la realtà mista di Windows.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realtà mista, movimenti, interazione, progettazione, cuffie per realtà mista, cuffie con realtà mista di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, Bloom
ms.openlocfilehash: 9e29d483375db103cebc30be9117e40899a9f81f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009431"
---
# <a name="start-gesture"></a>Azione di avvio

Il gesto di avvio è un movimento della mano usato per richiamare il menu Start. È l'equivalente di premere il tasto Windows sulle tastiere, il pulsante Xbox nei controller Xbox o il pulsante Windows sui controller di movimento per le cuffie immersive. Prestare particolare attenzione ai movimenti del sistema riservati in ogni dispositivo di realtà mista per evitare conflitti durante la progettazione delle interazioni.

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
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
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
        <td>Pulsante polso</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Occhio e palmare</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Fioritura

Abbiamo progettato "Bloom" per visualizzare il menu Start in HoloLens (1st Gen), che è un gesto simbolico che simula un fiore fiorito. Si tratta di un'operazione distinta per l'interazione sicura, facile da usare e rapida da richiamare. Per usare il movimento, è possibile passare da una palma all'altra, quindi aprire la mano, diffondendo le dita.

:::row:::
    :::column:::
        ![Bloom close](images/bloom-close.png)<br>
        **Passaggio 1: palmare insieme**<br>
    :::column-end:::
    :::column:::
        ![Sbocciare aperto](images/bloom-open.png)<br>
        **Passaggio 2: Palm up con la distribuzione a portata di mano**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Azione di avvio

In HoloLens 2, il movimento Bloom è stato sostituito con un pulsante di polso virtuale, che è più istintivo per gli utenti. Visualizzando gli utenti con il pulsante del polso, è possibile accedervi in modo intuitivo e premerlo con l'altra parte.

:::row:::
    :::column:::
        ![Pulsante del polso pronto](images/wrist-button-ready.png)<br>
        **Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**<br>
    :::column-end:::
    :::column:::
        ![Pressione del pulsante del polso](images/wrist-button-press.png)<br>
        **Passaggio 2: premere il pulsante del polso**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>Gesto iniziale a una mano

> [!IMPORTANT]
> Per il funzionamento del movimento iniziale a una sola mano:
>
> 1. È necessario eseguire l'aggiornamento all'aggiornamento di novembre 2019 (Build 18363,1039) o versione successiva.
> 1. È necessario calibrare gli occhi del dispositivo in modo che funzionino correttamente. Se non vengono visualizzati punti orbitanti intorno all'icona di avvio quando si esaminano i punti, gli occhi non vengono calibrati sul dispositivo.

È anche possibile usare il gesto di avvio con una sola mano. Si tenga presente che la Palma si trova in corrispondenza dell'icona di **avvio** sul polso interno. **Tenendo sempre d'occhio l'icona**, pizzicare il pollice e l'indice insieme.<br>
:::row:::
    :::column:::
        ![Pulsante del polso pronto](images/wrist-button-ready.png)<br>
        **Passaggio 1: eseguire il Palm up per visualizzare il pulsante del polso**<br>
    :::column-end:::
    :::column:::
        ![Pizzico pulsante polso](images/wrist-button-pinch.png)<br>
        **Passaggio 2: osservare il pulsante e quindi pizzicare**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Vedere anche

* [Interazioni istintive](interaction-fundamentals.md)
* [Sguardo attento](eye-tracking.md)
* [Input vocale](voice-input.md)
