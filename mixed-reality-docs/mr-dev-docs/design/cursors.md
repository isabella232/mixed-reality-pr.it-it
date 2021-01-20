---
title: Cursori
description: Un cursore, o un indicatore del vettore di destinazione, fornisce un feedback continuo all'utente per comprendere quali sono le intenzioni di HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1st Gen), HoloLens 2, realtà mista, cursori, targeting, sguardi, movimenti, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare in realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, raggi, input
ms.openlocfilehash: 0525bb9b30dfe71fba7b8ebf2afd2c87a8c97a27
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582401"
---
# <a name="cursors"></a>Cursori

![Cursori](images/UX_Hero_Cursor.jpg)

Un cursore fornisce un feedback continuo in base al punto in cui l'auricolare ritiene che lo stato attivo corrente degli utenti sia in un determinato momento. Il feedback del cursore include l'area, l'ologramma o il punto dell'ambiente virtuale che risponde all'input. Anche se il cursore è una rappresentazione digitale del punto in cui il dispositivo riconosce l'attenzione dell'utente, non è uguale alla determinazione delle intenzioni dell'utente. Il feedback del cursore consente inoltre agli utenti di sapere quali risposte di sistema prevedere. È possibile usare il feedback per comunicare la loro intenzione al dispositivo, aumentando la confidenza degli utenti.

Sono disponibili tre tipi di cursori: **Finger, Ray** e **Head-sguardi**. Questi puntatori funzionano con diverse modalità di input in HoloLens, HoloLens 2 e auricolari immersivi. Di seguito sono riportate informazioni aggiuntive sul tipo di cursore da usare per ogni tipo di modello di auricolare e interazione. Nel Toolkit di realtà mista (MRTK) sono stati creati moduli per i cursori con trascinamento della selezione che consentono di creare l'esperienza di puntamento corretta.

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
        <td>Cursore dito</td>
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
        <td>Cursore Head-sguardi</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Cursore dito

Il cursore Finger è disponibile solo in HoloLens 2 per migliorare la modalità di interazione "[manipolazione diretta con mani](direct-manipulation.md)". Sono stati collegati anelli ai suggerimenti di entrambi gli indici Fingers per comprendere meglio la posizione del dito. La dimensione dell'anello si basa sulla prossimità del dito alla superficie dell'interfaccia utente, che si riduce a un piccolo punto quando il dito tocca l'interfaccia utente. Maggiore è il dito, minore è l'anello. <br>

![cursore dito](images/finger-cursor.png)<br>
**Stati feedback visivi del cursore dito** 1: l'anello si riduce a un punto. 2: l'anello è allineato alla superficie. 3: l'anello è perpendicolare al vettore del dito. 4: nessun anello.

## <a name="ray-cursor"></a>Cursore Ray

I cursori raggio si allineano alla fine dei raggi di puntamento per consentire la manipolazione di oggetti fuori dalla portata di mano. Negli auricolari immersivi, i raggi vengono ritirati dai controller di movimento e terminano con i cursori a punti. In HoloLens 2 viene applicato il modello mentale di questi raggi del controller di movimento e i raggi mano progettati che hanno origine dalle palme e terminano con cursori a forma di anello coerenti con i cursori a dito usati nella manipolazione diretta. <br>
:::row:::
    :::column:::
        ![Controller del cursore Ray](images/ray-cursor-controller.png)<br>
        **Cursori Ray dei controller di movimento**<br>
    :::column-end:::
    :::column:::
        ![Mano del cursore Ray](images/ray-cursor-hand.png)<br>
        **Cursori raggio delle mani**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Cursore Head-sguardi

Il cursore Head-sguardi è un punto che si connette alla fine di un vettore di sguardi invisibili che usa la posizione e la rotazione dell'intestazione verso il punto. Per eseguire le azioni, questo cursore di puntamento è associato a diversi input di commit, ad esempio il tocco aereo, i comandi vocali, l'abitazione e la pressione del pulsante. In HoloLens 2, il punto di partenza è meglio abbinato a qualsiasi input di commit che non è un rubinetto d'aria, in quanto si verifica un conflitto di interazione tra il tocco aereo e i raggi di mano. <br>
:::row:::
    :::column:::
        ![Mano del cursore della testa](images/head-gaze-cursor-hand.png)<br>
        **Cursore Head-sguardi con movimento mano**<br>
    :::column-end:::
    :::column:::
        ![Voce cursore sguardo](images/head-gaze-cursor-voice.png)<br>
        **Cursore Head-sguardi con comando Voice**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Suggerimenti sulla personalizzazione del cursore

Se si desidera personalizzare i comportamenti e le caratteristiche di feedback del cursore, di seguito sono riportate alcune indicazioni sulla progettazione:

### <a name="cursor-scale"></a>Scala del cursore

* Il cursore non deve essere più grande delle destinazioni disponibili, consentendo agli utenti di interagire con facilità e di visualizzare il contenuto.
* A seconda dell'esperienza creata, il ridimensionamento del cursore mentre l'utente si trova è anche una considerazione importante. Ad esempio, man mano che l'utente ha una maggiore esperienza nell'esperienza, il cursore non dovrebbe diventare troppo piccolo in modo che vada perduto.
* Quando si ridimensiona il cursore, prendere in considerazione l'applicazione di un'animazione soft mentre viene ridimensionata in modo da ottenere un senso organico.
* Evitare di ostacolare il contenuto. Gli ologrammi sono gli elementi che rendono memorabile l'esperienza e il cursore non dovrebbe allontanarsi da essi.

### <a name="directionless-cursor-shape"></a>Forma cursore direzionale

* Sebbene non esista una forma di cursore corretta, è consigliabile usare una forma senza direzione come un toro. Un cursore che punta in una direzione, ad esempio un cursore a freccia tradizionale, potrebbe confondere l'utente in modo che sia sempre simile.
* Un'eccezione è rappresentata dall'utilizzo del cursore per la comunicazione dell'istruzione di interazione con l'utente. Ad esempio, quando si ridimensionano gli ologrammi nel sistema operativo di realtà mista, il cursore include temporaneamente frecce che indicano all'utente come spostare la mano per ridimensionare l'ologramma.

### <a name="look-and-feel"></a>Aspetto

* Un cursore a forma di ciambella o toro funziona per molte applicazioni.
* Selezionare un colore e una forma che rappresenti al meglio l'esperienza che si sta creando.
* I cursori sono particolarmente soggetti alla [separazione dei colori](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).
* Un piccolo cursore con opacità bilanciata mantiene informativo senza dominare la gerarchia visiva.
* Tenere presente che l'uso di ombre o evidenziazioni dietro il cursore potrebbe ostacolare il contenuto e distrarre dall'attività.
* I cursori devono allinearsi e abbracciare le superfici nell'app. Gli utenti avranno la sensazione che il sistema sia in grado di individuare il punto in cui si trovano, ma anche che il sistema sia in grado di riconoscere il proprio ambiente. Ad esempio, il cursore nel sistema operativo di realtà mista è allineato alle superfici del mondo dell'utente, creando una sensazione di consapevolezza del mondo anche quando l'utente non guarda direttamente un ologramma.
* Il blocco magnetico del cursore a un elemento interattivo quando è vicino all'utente può contribuire a migliorare la sicurezza che l'utente interagirà con tale elemento quando usa un'azione di selezione.

### <a name="visual-cues"></a>Segnali visivi

* Se l'esperienza è incentrata su un solo ologramma, il cursore dovrebbe allinearsi e abbracciare solo tale ologramma e modificare la forma quando si è lontani dall'ologramma. Ciò può comportare all'utente che l'ologramma è interoperabile e può interagire con esso.
* Se l'applicazione usa il mapping spaziale, il cursore potrebbe allinearsi e abbracciare ogni superficie che vede. In questo modo viene fornito un feedback agli utenti che HoloLens e l'applicazione possono visualizzare il proprio spazio. Questo rafforza il fatto che gli ologrammi sono reali e in questo mondo e contribuiscono a colmare il divario tra il reale e il virtuale.
* Avere un'idea di cosa deve fare il cursore quando non sono presenti ologrammi o superfici in visualizzazione. Il posizionamento a una distanza predeterminata davanti all'utente è un'opzione.

### <a name="possible-actions"></a>Azioni possibili

* Il cursore può essere rappresentato da icone diverse per indicare le possibili azioni che possono essere eseguite da un ologramma, ad esempio il ridimensionamento o la rotazione.
* Aggiungere al cursore informazioni aggiuntive solo se significa qualcosa per l'utente. In caso contrario, gli utenti potrebbero non osservare le modifiche dello stato o essere confuse dal cursore.

### <a name="input-state"></a>Stato input

* È possibile utilizzare il cursore per visualizzare lo stato o la finalità di input dell'utente. Ad esempio, è possibile visualizzare un'icona che informa l'utente che il sistema rileva lo stato della mano e che l'applicazione sa che è pronto a intervenire.
* È anche possibile usare il cursore per mostrare agli utenti che i comandi vocali sono stati uditi dal sistema con una modifica del colore momentanea

* Gli Stati del cursore seguenti possono essere implementati in modi diversi. È possibile implementare questi stati diversi modellando il cursore come una macchina a Stati. Ad esempio:
    * Lo stato di inattività è il punto in cui viene visualizzato il cursore predefinito.
    * Lo stato pronto è quando è stata rilevata la mano dell'utente nella posizione pronta.
    * Lo stato di interazione è quando l'utente sta eseguendo una particolare interazione.
    * Lo stato delle azioni possibili o il passaggio del mouse è quando si conferiscono azioni possibili che possono essere eseguite su un ologramma.

È anche possibile implementare questi stati in modo che possano visualizzare risorse dell'arte diverse quando si rilevano stati diversi.

<br>

---

## <a name="going-cursor-free"></a>"Senza cursore"

La progettazione senza cursore è consigliata quando il senso di immersione è un componente chiave di un'esperienza e quando si puntano interazioni (tramite sguardo e movimento) non è necessaria una precisione notevole. Il sistema deve comunque soddisfare i requisiti normali di un cursore: fornire agli utenti un feedback continuo sulla comprensione del sistema che punta e aiutarli a comunicare le proprie intenzioni al sistema. Questo può essere raggiungibile attraverso altre modifiche di stato evidenti.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cursore in MRTK (Mixed Reality Toolkit) per Unity

Per impostazione predefinita, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce una precostruzione del cursore ([DefaultCursor. prefabbricate](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) che ha lo stesso stato di visualizzazione del cursore di sistema della shell. Tale file viene assegnato in Pointers (Puntatori) nel profilo di input di MRTK. È possibile sostituire o personalizzare questo cursore per la propria esperienza. Per l'esperienza con l'input di rilevamento degli occhi, MRTK fornisce anche EyeGazeCursor, che presenta un oggetto visivo sottile per ridurre al minimo la distrazione.

* [MRTK - Profilo del puntatore](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK - Sistema di input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK - Puntatori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a>Vedi anche

* [Movimenti](gaze-and-commit.md#composite-gestures)
* [Puntamento con la testa e commit](gaze-and-commit.md)