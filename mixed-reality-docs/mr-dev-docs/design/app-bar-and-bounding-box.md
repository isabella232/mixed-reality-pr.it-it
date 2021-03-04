---
title: Rettangolo di selezione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realtà mista di Windows, barra delle applicazioni, rettangolo di delimitazione, cuffie per realtà mista, auricolare di realtà mista di Windows, headset di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: aba2e318439fec2bbb9e986c2ff7cac7a8a5fb3a
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759437"
---
# <a name="bounding-box-and-app-bar"></a>Rettangolo di selezione e barra dell'app
![Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>Che cos'è il rettangolo di delimitazione?

Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista. Questa funzionalità fornisce all'utente un segnale visivo che l'oggetto è attualmente modificabile. In HoloLens 2 il rettangolo di delimitazione funziona con la manipolazione diretta della mano e risponde alla vicinanza finger's dell'utente. Mostra commenti visivi per aiutare l'utente a percepire la distanza dall'oggetto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Ridimensionamento di un oggetto<br>
        Gli angoli del rettangolo di delimitazione indicano all'utente che l'oggetto può essere ridimensionato. Gli handle seguono un modello molto noto per la regolazione della scala. Questo segnale visivo Mostra agli utenti l'area totale dell'oggetto, anche se non è visibile al di fuori di una modalità di regolazione. Senza questa funzionalità, un oggetto bloccato a un altro oggetto o a una superficie può sembrare un comportamento simile a quello di uno spazio che non dovrebbe essere presente.<br>
        <br>
        *Ciclo video: ridimensionamento di un oggetto tramite il rettangolo di delimitazione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens punto di vista della scalabilità di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Rotazione di un oggetto<br>
        Il affordances rettangolare verticale sui bordi del rettangolo di delimitazione sono indicatori di rotazione. In questo modo l'utente garantisce una maggiore regolazione degli ologrammi posizionati. Non solo è possibile modificare e ridimensionare, ma ora ruotare anche.<br>
        <br>
        *Ciclo video: rotazione di un oggetto tramite il rettangolo di delimitazione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens punto di visualizzazione della rotazione di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Feedback visivo sulle prossimità della mano su HoloLens 2<br>
        In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione dell'utente della profondità. Un anello vicino alla loro parte viene visualizzato e ridimensionato quando il dito si avvicina all'oggetto. L'anello alla fine converge in un punto quando viene raggiunto lo stato premuto. Questa convenienza visiva consente all'utente di comprendere la distanza dall'oggetto.<br>
        <br>
        *Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di delimitazione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Feedback visivo sulla prossimità della mano](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Per lo sviluppo di app Unity, vedere [il riquadro delimitatore in Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>Che cos'è la barra dell'app?

La barra dell'app è un menu a livello di oggetto che contiene una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma. Questo modello viene in genere usato per consentire agli utenti di rimuovere e modificare gli ologrammi. La barra dell'app è stata progettata principalmente per gestire gli oggetti posizionati nell'ambiente di un utente. Insieme al rettangolo di delimitazione, un utente ha il controllo completo sulla posizione e sulla modalità di orientamento degli oggetti in realtà mista.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barra dell'app segue l'utente<br>
        Poiché questo modello viene usato con oggetti bloccati dal mondo, quando un utente si sposta intorno all'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente. Anche se non si tratta tecnicamente di un tabellone, questa funzionalità consente di ottenere lo stesso risultato. Impedire la posizione di un utente per occludere o bloccare la funzionalità che altrimenti sarebbe disponibile da una posizione diversa nell'ambiente. <br>
        <br>
        *Ciclo video: aggirare un ologramma, la barra dell'app segue*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Aggirare un ologramma. Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Rettangolo di delimitazione in MRTK (Mixed Reality Toolkit) per Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce script e prefabbricati per il rettangolo di delimitazione e la barra dell'app. È possibile aggiungere un rettangolo di delimitazione assegnando lo script BoundingBox.cs su qualsiasi oggetto.

* [MRTK-rettangolo di delimitazione](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md)


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
