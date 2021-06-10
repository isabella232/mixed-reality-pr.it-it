---
title: Rettangolo di selezione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra dell'app, rettangolo di selezione, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 750fb238e5b7f22998a86f71607498c8f6982076
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600520"
---
# <a name="bounding-box-and-app-bar"></a>Rettangolo di selezione e barra dell'app
![Il delimitazione è l'interfaccia standard per la manipolazione degli oggetti in realtà mista.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>Che cos'è il rettangolo di selezione?

Il delimitazione è l'interfaccia standard per la manipolazione degli oggetti in realtà mista. Questa funzionalità fornisce all'utente un segnale visivo che indica che l'oggetto è attualmente regolabile. Al HoloLens 2, il rettangolo di selezione funziona con la manipolazione diretta della mano e risponde alla prossimità del dito dell'utente. Mostra un feedback visivo per aiutare l'utente a percepire la distanza dall'oggetto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Ridimensionamento di un oggetto<br>
        Gli angoli del rettangolo di selezione indicano all'utente che l'oggetto può essere ridimensionato. Gli handle seguono un modello ampiamente noto per la regolazione della scala. Questo segnale visivo mostra agli utenti l'area totale dell'oggetto, anche se non è visibile all'esterno di una modalità di regolazione. Senza questa funzionalità, un oggetto agganciato a un altro oggetto o superficie può sembrare comportarsi come se ci fosse spazio intorno a esso che non dovrebbe essere presente.<br>
        <br>
        *Ciclo video: Ridimensionamento di un oggetto tramite rettangolo di selezione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Punto di visualizzazione di HoloLens per ridimensionare un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Rotazione di un oggetto<br>
        Gli affordance rettangolari verticali sui bordi del rettangolo di selezione sono indicatori di rotazione. In questo modo, l'utente può regolare in modo più fine gli ologrammi posizionati. Non solo possono regolare e ridimensionare, ma anche ruotare.<br>
        <br>
        *Ciclo video: Rotazione di un oggetto tramite rettangolo di selezione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Punto di visualizzazione di HoloLens per la rotazione di un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Feedback visivo sulla prossimità della mano HoloLens 2<br>
        In HoloLens 2, c'è un ulteriore segnale visivo, che può aiutare la percezione della profondità dell'utente. Un anello vicino alla punta del dito viene visualizzato e ridimensionato man mano che la punta del dito si avvicina all'oggetto. L'anello converge infine in un punto quando viene raggiunto lo stato premuto. Questo affordance visivo consente all'utente di comprendere la distanza dall'oggetto.<br>
        <br>
        *Ciclo video: esempio di feedback visivo in base alla prossimità a un rettangolo di selezione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Feedback visivo sulla prossimità della mano](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Per lo sviluppo di app Unity, vedere [Rettangolo di selezione in Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>Che cos'è la barra dell'app?

La barra dell'app è un menu a livello di oggetto, che contiene una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma. Questo modello viene comunemente usato per consentire agli utenti di rimuovere e regolare gli ologrammi. La barra dell'app è stata progettata principalmente come modo per gestire gli oggetti posizionati nell'ambiente di un utente. Insieme al rettangolo di selezione, un utente ha il controllo completo su dove e come gli oggetti sono orientati nella realtà mista.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barra dell'app segue l'utente<br>
        Poiché questo modello viene usato con oggetti bloccati a livello mondiale, quando un utente si sposta intorno all'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente. Anche se non tecnicamente, questa funzionalità ottiene in modo efficace lo stesso risultato. Impedire la posizione di un utente per occludere o bloccare funzionalità altrimenti disponibili da una posizione diversa nel proprio ambiente. <br>
        <br>
        *Ciclo video: in giro per un ologramma, la barra dell'app segue*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![In giro per un ologramma. Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)<br>
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