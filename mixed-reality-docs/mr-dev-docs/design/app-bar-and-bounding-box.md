---
title: Rettangolo di selezione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra dell'app, rettangolo di selezione, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: d7cacdcffeb552595e4ffd5ea5d1a734efb0451e03c5b6d5d39e5ea8caf3bd94
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198713"
---
# <a name="bounding-box-and-app-bar"></a>Rettangolo di selezione e barra dell'app
![Il delimitazione è l'interfaccia standard per la manipolazione degli oggetti nella realtà mista.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>Che cos'è il rettangolo di selezione?

Il delimitazione è l'interfaccia standard per la manipolazione degli oggetti nella realtà mista. Questa funzionalità fornisce all'utente un segnale visivo che indica che l'oggetto è attualmente regolabile. In HoloLens 2, il rettangolo di selezione funziona con la manipolazione diretta della mano e risponde alla prossimità del dito dell'utente. Mostra un feedback visivo per aiutare l'utente a percepire la distanza dall'oggetto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Ridimensionamento di un oggetto<br>
        Gli angoli del rettangolo di selezione indicano all'utente che l'oggetto può essere ridimensionato. Gli handle seguono un modello ampiamente noto per la regolazione della scala. Questo segnale visivo mostra agli utenti l'area totale dell'oggetto, anche se non è visibile al di fuori di una modalità di regolazione. Senza questa funzionalità, un oggetto ancorato a un altro oggetto o a un'altra superficie potrebbe sembrare che ci sia spazio intorno a esso che non dovrebbe essere presente.<br>
        <br>
        *Ciclo video: Ridimensionamento di un oggetto tramite rettangolo di selezione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens punto di vista del ridimensionamento di un oggetto tramite il rettangolo di selezione](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Rotazione di un oggetto<br>
        Gli affordance rettangolari verticali sui bordi del rettangolo di selezione sono indicatori di rotazione. Ciò offre all'utente una regolazione più fine rispetto agli ologrammi posizionati. Non solo possono regolare e ridimensionare, ma ora anche ruotare.<br>
        <br>
        *Ciclo video: rotazione di un oggetto tramite rettangolo di selezione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens punto di vista della rotazione di un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Feedback visivo sulla prossimità manuale HoloLens 2<br>
        In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione della profondità da parte dell'utente. Un anello vicino alla punta del dito viene visualizzato e ridimensionato man mano che la punta del dito si avvicina all'oggetto. L'anello converge infine in un punto quando viene raggiunto lo stato premuto. Questo oggetto visivo consente all'utente di comprendere quanto sono distasi dall'oggetto.<br>
        <br>
        *Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di selezione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Feedback visivo sulla prossimità manuale](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Per lo sviluppo di app Unity, vedi Rettangolo di selezione nel riquadro Realtà [mista Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**

<br>

---

## <a name="what-is-the-app-bar"></a>Che cos'è la barra dell'app?

La barra dell'app è un menu a livello di oggetto che contiene una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma. Questo modello viene comunemente usato per consentire agli utenti di rimuovere e modificare gli ologrammi. La barra dell'app è stata progettata principalmente come un modo per gestire gli oggetti posizionati nell'ambiente di un utente. Insieme al rettangolo di selezione, un utente ha il controllo completo su dove e come gli oggetti sono orientati nella realtà mista.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barra dell'app segue l'utente<br>
        Poiché questo modello viene usato con oggetti bloccati a livello mondiale, quando un utente si sposta all'esterno dell'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente. Anche se tecnicamente non si tratta di un'operazione di questo tipo, questa funzionalità consente di ottenere lo stesso risultato. Impedire la posizione di un utente per occludere o bloccare funzionalità che altrimenti sarebbero disponibili da una posizione diversa nel proprio ambiente. <br>
        <br>
        *Ciclo video: in un ologramma, la barra dell'app segue*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Spostarsi in un ologramma. Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Rettangolo di selezione in MRTK (Mixed Reality Toolkit) per Unity
**[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity)** script e prefab per il rettangolo di selezione e la barra dell'app. È possibile aggiungere un rettangolo di selezione assegnando lo script BoundingBox.cs a qualsiasi oggetto.

* [MRTK - Rettangolo di selezione](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a>Vedi anche

* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)