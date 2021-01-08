---
title: Visualizzazioni delle app
description: 'Informazioni su come usare i due tipi di visualizzazioni nelle app per la realtà mista di Windows: viste immersive e visualizzazioni 2D.'
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: visualizzazione immersiva, visualizzazione 2D, lavagna, app, cuffie per realtà mista, cuffie con realtà mista di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: a9cd03212fcbb0d7b3d9e4d2b3108e4d09972455
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009631"
---
# <a name="app-views"></a>Visualizzazioni delle app

Le app di Windows possono contenere due tipi di visualizzazioni: **viste immersive** e **visualizzazioni 2D**. Le app possono passare tra le diverse visualizzazioni immersive e 2D, mostrando le visualizzazioni 2D in un monitor come una finestra o in una cuffia come una lavagna. Le app con almeno una visualizzazione immersiva vengono categorizzate come **app realtà miste**. Le app che non hanno mai una visualizzazione Immersive sono **app 2D**.

## <a name="immersive-views"></a>Viste immersive

Una visualizzazione Immersive offre all'app la possibilità di creare ologrammi nel mondo circostante o di immergere l'utente in un ambiente virtuale. Quando un'app viene disegnata nella visualizzazione immersiva, nessun'altra app disegna allo stesso tempo gli &mdash; ologrammi di più app non sono composti insieme. Modificando continuamente la prospettiva da cui l' [app esegue il rendering](../develop/platform-capabilities-and-apis/rendering.md) della scena in modo che corrisponda ai movimenti Head dell'utente, l'app può eseguire il rendering di ologrammi a [blocchi internazionali](coordinate-systems.md) . Gli ologrammi con blocco mondiale restano in un punto fisso nel mondo reale oppure possono eseguire il rendering di un mondo virtuale che mantenga la posizione in cui si sposta l'utente.

![In una visualizzazione immersiva, gli ologrammi possono essere posizionati in tutto il mondo.](images/designoverview-940px.jpg)<br>
*In una visualizzazione immersiva, gli ologrammi possono essere posizionati in tutto il mondo*

In [HoloLens](https://docs.microsoft.com/hololens/hololens1-hardware)l'app esegue il rendering degli ologrammi sopra gli ambienti reali dell'utente. In una [serie di cuffie a realtà mista di Windows](../discover/immersive-headset-hardware-details.md), l'utente non può vedere il mondo reale, quindi l'app deve eseguire il rendering di tutti gli elementi visualizzati dall'utente.

La [Home realtà mista di Windows](../discover/navigating-the-windows-mixed-reality-home.md) (inclusi il menu Start e gli ologrammi posizionati intorno all'ambiente) non viene visualizzata in una visualizzazione immersiva. In HoloLens, Cortana inoltra tutte le notifiche di sistema che si verificano durante la visualizzazione di una visualizzazione immersiva, a cui l'utente può rispondere con l'input vocale.

In una visualizzazione immersiva, l'app è anche responsabile della gestione di tutti gli input. L'input nella realtà mista di Windows è costituito da [sguardi](gaze-and-commit.md), [movimenti](gaze-and-commit.md#composite-gestures) (solo HoloLens), [Voice and [Motion Controllers](motion-controllers.md) (solo cuffie immersive).

## <a name="2d-views"></a>visualizzazioni 2D

![Più visualizzazioni 2D disposte intorno alla Home realtà mista di Windows](images/teleportation-940px.png)<br>
*Più app con una visualizzazione 2D posizionata intorno alla Home realtà mista di Windows*

Un'app con una visualizzazione 2D viene visualizzata nella [Home realtà mista di Windows](../discover/navigating-the-windows-mixed-reality-home.md) (talvolta chiamata "Shell") come Slate virtuale, sottoposta a rendering insieme ai lanci di app e ad altri ologrammi che l'utente ha inserito nel proprio mondo. L'utente può modificare questo Slate per spostarlo e ridimensionarlo, sebbene rimanga a una risoluzione fissa indipendentemente dalle dimensioni. Se la prima visualizzazione dell'app è una visualizzazione 2D, il contenuto 2D verrà riempito dallo stesso Slate usato per avviare l'app.

In una cuffia desktop è possibile eseguire le app piattaforma UWP (Universal Windows Platform) (UWP) che vengono eseguite attualmente sul monitor desktop. Queste app già eseguono il rendering delle visualizzazioni 2D e il relativo contenuto verrà visualizzato automaticamente in uno Slate nel mondo dell'utente all'avvio. le app UWP 2D possono essere destinate alla famiglia di dispositivi **Windows. universali** per l'esecuzione sia su cuffie Desktop sia su HoloLens come Slate.

Un uso chiave delle visualizzazioni 2D mostra un modulo di immissione di testo che usa la tastiera di sistema. Poiché non è possibile eseguire il rendering della shell sopra una visualizzazione immersiva, l'app deve passare a una visualizzazione 2D per visualizzare la tastiera di sistema. Le app che vogliono accettare input di testo devono passare a una visualizzazione 2D con una casella di testo. Quando tale casella di testo ha lo stato attivo, il sistema Visualizza la tastiera di sistema, consentendo all'utente di immettere testo.

Un'app può avere visualizzazioni 2D sia sul monitor desktop che su un auricolare collegato in un computer desktop. È possibile, ad esempio, esplorare Edge sul monitor desktop usando la visualizzazione 2D principale per trovare un video di 360 gradi. Quando si riproduce il video, Edge avvierà una visualizzazione immersiva secondaria all'interno dell'auricolare per visualizzare il contenuto video immersivo.

## <a name="see-also"></a>Vedere anche

* [Modello di app](app-model.md)
* [Aggiornamento di app UWP 2D per la realtà mista](../develop/porting-apps/building-2d-apps.md)
* [Ottenere un HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)
* [Tipi di app di realtà mista](types-of-mixed-reality-apps.md)
