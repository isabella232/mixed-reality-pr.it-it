---
title: Cursori
description: Un cursore, o indicatore del vettore di destinazione, fornisce un feedback continuo per l'utente per comprendere HoloLens informazioni sulle intenzioni.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (prima generazione), HoloLens 2, realtà mista, cursori, destinazione, sguardo, movimenti, visore di realtà mista, visore di realtà mista windows, visore per realtà virtuale, HoloLens, MRTK, Toolkit, raggi, input
ms.openlocfilehash: 46e570328451078586109448bce28a7074bc9c2f791c15a284c85b845441fabe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187058"
---
# <a name="cursors"></a>Cursori

![Cursori](images/UX_Hero_Cursor.jpg)

Un cursore fornisce feedback continuo in base al punto in cui il visore ritiene che lo stato attivo corrente degli utenti sia in un determinato momento. Il feedback del cursore include l'area, l'ologramma o il punto nell'ambiente virtuale che risponde all'input. Anche se il cursore è una rappresentazione digitale di dove il dispositivo comprende l'attenzione dell'utente, questo non è lo stesso di determinare le intenzioni dell'utente. Il feedback del cursore consente inoltre agli utenti di conoscere le risposte del sistema previste. È possibile usare i commenti e suggerimenti per comunicare l'intenzione al dispositivo, in modo da aumentare l'attendibilità degli utenti.

Sono disponibili tre tipi di cursori: **dito, raggio** e **sguardo alla testa.** Questi cursori di puntamento funzionano con diverse modalità di input HoloLens, HoloLens 2 visori immersivi. Di seguito sono riportate indicazioni sul tipo di cursore da usare per ogni tipo di visore e modello di interazione. In Mixed Reality Toolkit (MRTK) sono stati creati moduli di cursori di trascinamento della selezione per creare l'esperienza di puntamento più utile.

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
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Cursore del dito</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Cursore Ray</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursore con sguardo rivolto verso la testa</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Cursore del dito

Il cursore del dito è disponibile solo nel HoloLens 2 per migliorare la modalità di interazione " manipolazione diretta[con](direct-manipulation.md)le mani ". Sono stati collegati anelli alle punte di entrambe le dita dell'indice per comprendere meglio dove punta il dito. Le dimensioni dell'anello si basano sulla prossimità del dito alla superficie dell'interfaccia utente, che si riduce a un piccolo punto quando il dito tocca l'interfaccia utente. Più vicino è il dito, più piccolo è l'anello. <br>

![Cursore dito](images/finger-cursor.png)<br>
**Stati di feedback visivo del cursore dito** 1: l'anello si riduce a un punto. 2: l'anello è allineato alla superficie. 3: l'anello è perpendicolare al vettore delle dita. 4: Nessun anello.

## <a name="ray-cursor"></a>Cursore Ray

I cursori di raggio si collegano alla fine dei raggi che puntano lontano per consentire la manipolazione di oggetti non raggiungibili. Nei visori immersivi, i raggi si distoglieno dai controller di movimento e terminano con cursori punto. In HoloLens 2, si applica il modello mentale di questi raggi controller del movimento e i raggi della mano progettati che provengono dai palmi e terminano in cursori a forma di anello coerenti con i cursori del dito usati nella manipolazione diretta. <br>
:::row:::
    :::column:::
        ![Controller cursore Ray](images/ray-cursor-controller.png)<br>
        **Cursori a raggi dei controller di movimento**<br>
    :::column-end:::
    :::column:::
        ![Mano del cursore Ray](images/ray-cursor-hand.png)<br>
        **Cursori di raggio delle mani**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Cursore con sguardo rivolto verso la testa

Il cursore con sguardo rivolto verso la testa è un punto che si collega alla fine di un vettore di punta invisibile che usa la posizione e la rotazione della testa verso il punto. Per eseguire azioni, questo cursore di puntamento è associato a vari input di commit, ad esempio il tocco dell'aria, i comandi vocali, la sospensione e la pressione del pulsante. In HoloLens 2, lo sguardo alla testa è meglio abbinato a qualsiasi input di commit che non sia un tocco dell'aria, in quanto si verifica un conflitto di interazione tra il tocco dell'aria e i raggi di estrema mano. <br>
:::row:::
    :::column:::
        ![Mano del cursore con lo sguardo rivolto verso la testa](images/head-gaze-cursor-hand.png)<br>
        **Cursore con sguardo rivolto verso la testa con movimento della mano**<br>
    :::column-end:::
    :::column:::
        ![Voce del cursore dello sguardo rivolto verso la testa](images/head-gaze-cursor-voice.png)<br>
        **Cursore head-gaze con comando vocale**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Raccomandazioni per la personalizzazione del cursore

Per personalizzare i comportamenti e gli aspetti del feedback del cursore, ecco alcuni consigli di progettazione:

### <a name="cursor-scale"></a>Scala del cursore

* Il cursore non deve essere più grande delle destinazioni disponibili, consentendo agli utenti di interagire facilmente con e visualizzare il contenuto.
* A seconda dell'esperienza creata, anche il ridimensionamento del cursore quando l'utente guarda intorno è una considerazione importante. Ad esempio, man mano che l'utente guarda più lontano nell'esperienza, il cursore non deve diventare troppo piccolo in modo che sia perso.
* Quando si ridimensiona il cursore, è consigliabile applicarvi un'animazione soft man mano che viene ridimensionata per dare un'emozione organica.
* Evitare di ostruire il contenuto. Ologrammi sono ciò che rende l'esperienza facile da ricordare e il cursore non deve essere rimosso da essi.

### <a name="directionless-cursor-shape"></a>Forma cursore senza direzione

* Anche se non è presente una sola forma di cursore a destra, è consigliabile usare una forma senza direzione, ad esempio un toro. Un cursore che punta in una direzione (ad esempio, un cursore a freccia tradizionale) potrebbe confondere l'utente in modo da avere sempre un aspetto simile.
* Un'eccezione a questo problema si verifica quando si usa il cursore per comunicare l'istruzione di interazione all'utente. Ad esempio, quando si ridimensionano gli ologrammi nel sistema operativo Mixed Reality, il cursore include temporaneamente frecce che indica all'utente come spostare la mano per ridimensionare l'ologramma.

### <a name="look-and-feel"></a>Aspetto

* Un cursore a forma di ciambella o toro funziona per molte applicazioni.
* Selezionare un colore e una forma che rappresentino al meglio l'esperienza che si sta creando.
* I cursori sono particolarmente inclini alla [separazione dei colori.](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* Un cursore di piccole dimensioni con opacità bilanciata lo mantiene informativo senza dominare la gerarchia visiva.
* È importante usare ombreggiature o evidenziazioni dietro il cursore perché potrebbero ostacolare il contenuto e distrarre dall'attività a portata di mano.
* I cursori devono essere allineati e abbracciati alle superfici nell'app. Gli utenti avranno la consapevolezza che il sistema può vedere dove stanno cercando, ma anche che il sistema è a conoscenza dell'ambiente circostante. Ad esempio, il cursore nel sistema operativo realtà mista si allinea alle superfici del mondo dell'utente, creando una consapevolezza del mondo anche quando l'utente non guarda direttamente a un ologramma.
* Il blocco magnetico del cursore su un elemento interattivo quando è vicino all'utente può contribuire a migliorare l'attendibilità dell'interazione dell'utente con tale elemento quando usa un'azione di selezione.

### <a name="visual-cues"></a>Visivi

* Se l'esperienza è incentrata su un singolo ologramma, il cursore deve allinearsi e abbracciare solo l'ologramma e cambiare forma quando si guarda lontano da tale ologramma. Questo può comunicare all'utente che l'ologramma è fattibile e può interagire con esso.
* Se l'applicazione usa il mapping spaziale, il cursore potrebbe allinearsi e abbracciare ogni superficie visualizzata. In questo modo si inviano commenti e suggerimenti agli utenti HoloLens l'applicazione può visualizzare il proprio spazio. Questo rinforza il fatto che gli ologrammi sono reali e nel nostro mondo e contribuisce a colmare il divario tra reale e virtuale.
* Avere un'idea di cosa deve fare il cursore quando non sono presenti ologrammi o superfici in vista. Posizionarlo a una distanza predeterminata davanti all'utente è un'opzione.

### <a name="possible-actions"></a>Azioni possibili

* Il cursore può essere rappresentato da icone diverse per trasmettere le possibili azioni che un ologramma può eseguire, ad esempio il ridimensionamento o la rotazione.
* Aggiungere informazioni aggiuntive sul cursore solo se significa qualcosa per l'utente. In caso contrario, gli utenti potrebbero non notare le modifiche dello stato o essere confusi dal cursore.

### <a name="input-state"></a>Stato di input

* È possibile usare il cursore per visualizzare lo stato o la finalità di input dell'utente. Ad esempio, è possibile visualizzare un'icona che indica all'utente che il sistema vede lo stato della mano e che l'applicazione sa di essere pronta a intervenire.
* È anche possibile usare il cursore per mostrare agli utenti che i comandi vocali sono stati ascoltati dal sistema tramite una modifica momentanea del colore

* I seguenti stati del cursore possono essere implementati in modi diversi. È possibile implementare questi diversi stati modellando il cursore come una macchina a stati. Ad esempio:
    * Lo stato di inattività è il punto in cui viene visualizzato il cursore predefinito.
    * Lo stato Pronto è quando è stata rilevata la mano dell'utente nella posizione pronta.
    * Lo stato di interazione è quando l'utente sta eseguendo una particolare interazione.
    * Lo stato delle azioni possibili o lo stato del passaggio del mouse si verifica quando si comunicano le possibili azioni che possono essere eseguite su un ologramma.

È anche possibile implementare questi stati in modo skin-able per visualizzare asset di grafica diversi quando si rilevano stati diversi.

<br>

---

## <a name="going-cursor-free"></a>Andare "senza cursore"

La progettazione senza cursore è consigliata quando il senso dell'immersione è un componente chiave di un'esperienza e quando le interazioni di puntamento (tramite lo sguardo fisso e il movimento) non richiedono una grande precisione. Il sistema deve comunque soddisfare i normali requisiti di un cursore: fornire agli utenti un feedback continuo sulla comprensione del sistema e aiutare gli utenti a comunicare le proprie intenzioni al sistema. Questa operazione può essere possibile tramite altre modifiche di stato evidenti.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cursore in MRTK (Mixed Reality Toolkit) per Unity

Per impostazione predefinita, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce un prefab del cursore([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) che ha lo stesso stato di visualizzazione del cursore di sistema della shell. Tale file viene assegnato in Pointers (Puntatori) nel profilo di input di MRTK. È possibile sostituire/personalizzare questo cursore in base all'esperienza. Per l'esperienza con l'input di tracciamento oculare, MRTK offre anche EyeGazeCursor, che ha un oggetto visivo sottile per ridurre al minimo la distrazione.

* [MRTK - Profilo del puntatore](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK - Sistema di input](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK - Puntatori](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>Vedi anche

* [Movimenti](gaze-and-commit.md#composite-gestures)
* [Puntamento con la testa e commit](gaze-and-commit.md)