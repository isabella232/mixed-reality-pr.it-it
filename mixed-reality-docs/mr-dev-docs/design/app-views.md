---
title: Visualizzazioni delle app
description: 'Informazioni su come usare i due tipi di visualizzazioni nelle app Windows Mixed Reality: visualizzazioni immersive e visualizzazioni 2D.'
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: visualizzazione immersive, visualizzazione 2D, slate, app, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: 1f779749938bfc8893f0e1f1f60c97549d30a24075b5b0926af61e2f88625b9c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191513"
---
# <a name="app-views"></a>Visualizzazioni delle app

Windows possono contenere due tipi di visualizzazioni: **visualizzazioni immersive** e **visualizzazioni 2D.** Le app possono passare tra le diverse visualizzazioni immersive e 2D, visualizzando le visualizzazioni 2D su un monitor come finestra o in un visore VR come slate. Le app con almeno una visualizzazione immersiva sono classificate come **app di realtà mista.** Le app che non hanno mai una visualizzazione Immersive sono **app 2D**.

## <a name="immersive-views"></a>Visualizzazioni immersive

Una visualizzazione Immersive offre all'app la possibilità di creare ologrammi nel mondo circostante o di immergere l'utente in un ambiente virtuale. Quando un'app disegna nella visualizzazione immersiva, nessun'altra app disegna contemporaneamente ologrammi da più app non vengono &mdash; composti insieme. Modificando continuamente la prospettiva da cui [l'app](../develop/platform-capabilities-and-apis/rendering.md) esegue il rendering della scena in modo che corrisponda ai movimenti della testa dell'utente, l'app può eseguire il rendering di ologrammi bloccati dal mondo. [](coordinate-systems.md) Gli ologrammi bloccati a livello mondiale rimangono in un punto fisso del mondo reale o possono eseguire il rendering di un mondo virtuale che mantiene la propria posizione mentre un utente si sposta.

![In una visualizzazione immersiva, gli ologrammi possono essere posizionati nel mondo che ti circonda.](images/designoverview-940px.jpg)<br>
*In una visualizzazione immersiva, gli ologrammi possono essere posizionati nel mondo che ti circonda*

In [HoloLens](/hololens/hololens1-hardware), l'app esegue il rendering degli ologrammi sopra l'ambiente reale dell'utente. In un [Windows Mixed Reality vr immersive,](../discover/immersive-headset-hardware-details.md)l'utente non può visualizzare il mondo reale e quindi l'app deve eseguire il rendering di tutto ciò che l'utente vede.

Il [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (inclusi i menu Start e gli ologrammi posizionati intorno all'ambiente) non esegue il rendering in una visualizzazione immersiva. In HoloLens, Cortana inoltra le notifiche di sistema che si verificano durante la visualizzazione di una visualizzazione immersiva, a cui l'utente può rispondere con l'input vocale.

In una visualizzazione immersiva, l'app è anche responsabile della gestione di tutto l'input. L'input Windows Mixed Reality è costituito [](gaze-and-commit.md)da sguardo fisso, movimento [(solo](gaze-and-commit.md#composite-gestures) HoloLens), [controller vocali e del movimento [(solo](motion-controllers.md) visori VR immersive).

## <a name="2d-views"></a>Visualizzazioni 2D

![Più visualizzazioni 2D disposte intorno alla Windows Mixed Reality home](images/teleportation-940px.png)<br>
*Più app con una visualizzazione 2D posizionata intorno alla Windows Mixed Reality home*

Un'app con visualizzazione 2D viene visualizzata nella home page di [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) (talvolta denominata "shell") come uno slate virtuale, di cui viene eseguito il rendering insieme alle utilità di avvio delle app e ad altri ologrammi inseriti dall'utente nel proprio mondo. L'utente può modificare questo slate per spostarlo e ridimensionarlo, anche se rimane a una risoluzione fissa indipendentemente dalle dimensioni. Se la prima visualizzazione dell'app è una visualizzazione 2D, il contenuto 2D riempirà lo stesso slate usato per avviare l'app.

In un visore VR desktop è possibile eseguire qualsiasi app UWP (Universal Windows Platform) attualmente in esecuzione sul monitor desktop. Queste app stanno già visualizzando visualizzazioni 2D e il relativo contenuto verrà visualizzato automaticamente in uno slate nel mondo dell'utente all'avvio. Le app UWP 2D possono avere come destinazione **Windows. Famiglia** di dispositivi universali da eseguire sia su visori VR desktop che HoloLens come slate.

Un uso chiave delle visualizzazioni 2D è la visualizzazione di un modulo di immissione testo che usa la tastiera di sistema. Poiché non è possibile eseguire il rendering della shell sopra una visualizzazione immersiva, l'app deve passare a una visualizzazione 2D per visualizzare la tastiera di sistema. Le app che vogliono accettare l'input di testo devono passare a una visualizzazione 2D con una casella di testo. Mentre la casella di testo ha lo stato attivo, il sistema visualizza la tastiera di sistema, consentendo all'utente di immettere testo.

Un'app può avere visualizzazioni 2D sia sul monitor desktop che in un visore VR collegato in un PC desktop. Ad esempio, è possibile esplorare Microsoft Edge sul monitor desktop usando la visualizzazione 2D principale per trovare un video a 360 gradi. Quando si riproduce il video, Edge avvierà una visualizzazione immersiva secondaria all'interno del visore VR per visualizzare il contenuto del video immersive.

## <a name="see-also"></a>Vedi anche

* [Modello di app](app-model.md)
* [Aggiornamento di app UWP 2D per la realtà mista](../develop/porting-apps/building-2d-apps.md)
* [Ottenere un HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)
* [Tipi di app di realtà mista](types-of-mixed-reality-apps.md)