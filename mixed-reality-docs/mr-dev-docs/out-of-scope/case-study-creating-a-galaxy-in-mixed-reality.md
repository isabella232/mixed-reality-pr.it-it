---
title: Case study - Creazione di una galaxy nella realtà mista
description: Informazioni sull'applicazione "Galaxy Explorer" e su come è stata creata per microsft HoloLens e dopo un sondaggio su Twitter di 24 ore da parte degli sviluppatori della community.
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, condividere l'idea, case study
ms.openlocfilehash: 5891fbc052c52cd90176214d1eff8ef019a2bcfc80dbd5264489deced0fb1664
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208084"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Case study - Creazione di una galaxy nella realtà mista

Prima Microsoft HoloLens la spedizione, abbiamo chiesto alla community di sviluppatori quale tipo di app vorrebbe vedere un team interno esperto per il nuovo dispositivo. Sono state condivise più di 5000 idee e, dopo un sondaggio su Twitter di 24 ore, il vincitore è stato un'idea chiamata [Galaxy Explorer.](../develop/unity/galaxy-explorer.md)

Andy Zibits, il art lead del progetto, e Karim Luccin, il tecnico grafico del team, parla dell'impegno collaborativo tra arte e ingegneria che ha portato alla creazione di una rappresentazione accurata e interattiva della galaxy Milky Way in Galaxy Explorer.

## <a name="the-tech"></a>The Tech

Il [nostro team,](../develop/unity/galaxy-explorer.md#meet-the-team) costituito da due progettisti, tre sviluppatori, quattro autori, un produttore e un tester, ha avuto sei settimane di tempo per creare un'app completamente funzionale che consentisse agli utenti di conoscere ed esplorare la vastità e la creatività della nostra galaxy di Milky Way.

L'obiettivo era sfruttare appieno la capacità di HoloLens di eseguire il rendering di oggetti 3D direttamente nello spazio, quindi abbiamo deciso di creare una galaxy dall'aspetto realistico in cui le persone sarebbero state in grado di fare zoom avanti e vedere le singole stelle, ognuna con le proprie rispettive convivenze.

Nella prima settimana di sviluppo sono stati creati alcuni obiettivi per la rappresentazione della galaxy di Milky Way: era necessario avere profondità, movimento e volumetrica, piena di stelle che avrebbero potuto contribuire a creare la forma della luna.

Il problema della creazione di una galaxy animata con miliardi di stelle è che il numero elevato di singoli elementi che devono essere aggiornati sarebbe troppo grande per ogni fotogramma perché HoloLens animasse usando la CPU. La soluzione ha comportato una combinazione complessa di arte e scienza.

## <a name="behind-the-scenes"></a>Dietro le quinte

Per consentire agli utenti di esplorare singole stelle, il primo passaggio consisteva nel determinare il numero di particelle di cui è possibile eseguire il rendering in una sola volta.

### <a name="rendering-particles"></a>Particelle di rendering

Le CPU correnti sono molto efficaci per l'elaborazione di attività seriali e fino ad alcune attività parallele contemporaneamente (a seconda del numero di core disponibili), ma le GPU sono molto più efficaci nell'elaborazione di migliaia di operazioni in parallelo. Tuttavia, poiché in genere non condividono la stessa memoria della CPU, lo scambio di dati tra CPU<>GPU può diventare rapidamente un collo di bottiglia. La soluzione consisteva nel creare una galaxy sulla GPU e doveva essere completamente in grado di convivere con la GPU.

Sono stati avviati test di stress con migliaia di particelle di punti in vari modelli. In questo modo è stato possibile ottenere la HoloLens per vedere cosa ha funzionato e cosa non ha funzionato.

### <a name="creating-the-position-of-the-stars"></a>Creazione della posizione delle stelle

Uno dei membri del team ha già scritto il codice C# che generava stelle nella posizione iniziale. Le stelle sono su un'ellisse e la relativa posizione può essere descritta da (**curveOffset**, **ellipseSize**, **elevation**) dove **curveOffset** è l'angolo della stella lungo l'ellisse, **ellipseSize** è la dimensione dell'ellisse lungo X e Z ed elevazione dell'elevazione appropriata della stella all'interno della galaxy. È quindi possibile creare un buffer ([ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)di Unity ) che verrebbe inizializzato con ogni attributo star e inviarlo alla GPU in cui si trova per il resto dell'esperienza. Per disegnare questo buffer, si usa [DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) di Unity che consente di eseguire uno shader (codice su una GPU) su un set arbitrario di punti senza avere una mesh effettiva che rappresenta la galaxy:

**Cpu:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**Gpu:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Abbiamo iniziato con modelli circolari non elaborati con migliaia di particelle. Questo ci ha fornito la prova che era necessario gestire molte particelle ed eseguirla a velocità performanti, ma non siamo stati soddisfatti della forma complessiva della galaxy. Per migliorare la forma, sono stati tentati vari modelli e sistemi di particelle con rotazione. Inizialmente si tratta di particelle e prestazioni coerenti, ma la forma si è erta vicino al centro e le stelle emettevano all'esterno che non erano realistiche. Era necessaria un'emissione che consentisse di manipolare il tempo e fare in modo che le particelle si spostino in modo realistico, scorrendo sempre più vicino al centro della galaxy.

![Sono stati tentati vari modelli e sistemi di particelle che ruotavano, come questi.](images/galaxy-patterns-500px.png)

Sono stati tentati vari modelli e sistemi di particelle che ruotavano, come questi.

Il nostro team ha fatto alcune ricerche sul funzionamento delle onde d'aria ed è stato creato un sistema di particelle personalizzato specifico per la galaxy, in modo da poter spostare le particelle su ellissi in base alla["teoria](https://en.wikipedia.org/wiki/Density_wave_theory)delle onde di densità", che teorizza che le onde di una galaxy sono aree di densità più elevata, ma in flusso costante, come un ingorgo del traffico. Sembra stabile e solido, ma le stelle si spostano effettivamente all'interno e all'uscita delle braci mentre si spostano lungo le rispettive ellissi. Nel sistema, le particelle non esistono mai nella CPU: le schede vengono generate e orientate tutte nella GPU, quindi l'intero sistema è semplicemente lo stato iniziale + tempo. L'avanzamento è stato simile al seguente:

![Avanzamento del sistema di particelle con rendering GPU](images/spiral-galaxy-arms-500px.jpg)

Avanzamento del sistema di particelle con rendering GPU


Dopo aver aggiunto un numero sufficiente di puntini di sospensione e averne impostato la rotazione, le capovolgimenti iniziano a formare "leve" in cui il movimento delle stelle converge. Alla spaziatura delle stelle lungo ogni percorso ellittico è stata data una certa casualità e a ogni stella è stata aggiunta una certa casualità posizionale. In questo modo è stata creata una distribuzione dall'aspetto molto più naturale del movimento a stella e della forma del arm. Infine, è stata aggiunta la possibilità di guidare il colore in base alla distanza dal centro.

### <a name="creating-the-motion-of-the-stars"></a>Creazione del movimento delle stelle

Per animare il movimento a stella generale, è necessario aggiungere un angolo costante per ogni fotogramma e fare in modo che le stelle si spostino lungo le ellissi a una velocità radiale costante. Questo è il motivo principale per l'uso di **curveOffset.** Questo non è tecnicamente corretto perché le stelle si spostano più velocemente lungo i lati lunghi delle ellissi, ma il movimento generale è stato positivo.

![Le stelle si spostano più velocemente sull'arco lungo, più lente sui bordi.](images/ellipse-movement.jpg)

Le stelle si spostano più velocemente sull'arco lungo, più lente sui bordi.


In questo modo, ogni stella è completamente descritta da (**curveOffset**, **ellipseSize**, **elevation**, **Age**) dove **Age** è un accumulo del tempo totale passato dal caricamento della scena.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

In questo modo è stato possibile generare decine di migliaia di stelle una volta all'inizio dell'applicazione, quindi è stato animato un singolo set di stelle lungo le curve stabilite. Poiché tutto è presente nella GPU, il sistema può animare tutte le stelle in parallelo senza alcun costo per la CPU.

![Ecco come appare quando si disegnano quad bianchi.](images/drawing-white-quads-300px.jpg)

Ecco come appare quando si disegnano quad bianchi.



Per fare in modo che ogni quad faccia la fotocamera, è stato usato uno shader geometry per trasformare ogni posizione a stella in un rettangolo 2D sullo schermo che conterrà la trama a stella.

![Rombi anziché quad.](images/drawing-white-quads-300px.jpg)

Rombi anziché quad.


Poiché si vuole limitare il più possibile la sovrapposizione (numero di volte in cui verrà elaborato un pixel), i quad sono stati ruotati in modo che si sovrappongano meno.

### <a name="adding-clouds"></a>Aggiunta di cloud

Esistono diversi modi per ottenere una sensazione volumetrica con le particelle, dall'intasamento dei raggi all'interno di un volume al disegno del maggior numero possibile di particelle per simulare una nuvola. Il ray marching in tempo reale sarebbe stato troppo costoso e difficile da creare, quindi per la prima volta abbiamo provato a creare un sistema imposter usando un metodo per il rendering delle foreste nei giochi, con molte immagini 2D di alberi rivolti verso la fotocamera. Quando si esegue questa operazione in un gioco, è possibile eseguire il rendering di trame di alberi da una fotocamera che ruota intorno, salvare tutte le immagini e, in fase di esecuzione per ogni scheda di carte, selezionare l'immagine che corrisponde alla direzione di visualizzazione. Questo non funziona anche quando le immagini sono ologrammi. La differenza tra l'occhio sinistro e l'occhio destro fa sì che sia necessaria una risoluzione molto più elevata, in caso contrario sembra semplicemente semplice, con alias o ripetitiva.

Nel secondo tentativo si è provato ad avere il maggior numero possibile di particelle. Gli oggetti visivi migliori sono stati ottenuti quando le particelle sono state disegnate e sfocate in modo additivo prima di aggiungerle alla scena. I problemi tipici di questo approccio erano correlati al numero di particelle che è possibile disegnare contemporaneamente e alla quantità di area dello schermo coperta mantenendo comunque 60fps. La sfocatura dell'immagine risultante per ottenere questa impressione di cloud era in genere un'operazione molto disassura.

![Senza trama, questa è l'aspetto delle cloud con opacità del 2%.](images/clouds-without-texture-300px.jpg)

Senza trama, questa è l'aspetto delle cloud con opacità del 2%.



Essere additivi e avere molti di essi significa che ci sarebbero diversi quad uno sopra l'altro, ombreggiatendo ripetutamente lo stesso pixel. Al centro della galaxy, lo stesso pixel ha centinaia di quad l'uno sopra l'altro e questo ha avuto un costo enorme quando l'operazione viene eseguita a schermo intero.

L'uso di cloud a schermo intero e il tentativo di sfocatura sarebbe stata una pessima idea, quindi abbiamo deciso di lasciare che l'hardware faccia il lavoro per noi.

### <a name="a-bit-of-context-first"></a>Un po' di contesto per primo

Quando si usano trame in un gioco, le dimensioni della trama raramente corrispondono all'area in cui si vuole usarla, ma è possibile usare diversi tipi di filtro della trama per ottenere la scheda grafica per interpolare il colore desiderato dai pixel della trama[(filtro](/previous-versions/visualstudio/visual-studio-2015/debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)trama). Il filtro che interessa è il [filtro bilineare](/windows/win32/direct3d9/bilinear-texture-filtering) che calcola il valore di qualsiasi pixel usando i 4 vicini più prossimi.

![Originale prima del filtro](images/texture-1.png)

![Risultato dopo il filtro](images/texture-2.png)

Usando questa proprietà, si può vedere che ogni volta che si prova a disegnare una trama in un'area due volte più grande, il risultato viene sfocato.

Invece di eseguire il rendering a schermo intero e perdere i millisecondi preziose che si potrebbero perdere per un altro elemento, viene eseguito il rendering in una piccola versione dello schermo. Quindi, copiando questa trama e estenderla di un fattore di 2 volte, si torna allo schermo intero sfocando il contenuto nel processo.

![Il ridimensionamento x3 torna alla risoluzione completa.](images/galaxy-resolutions-300px.png)

Il ridimensionamento x3 torna alla risoluzione completa.



Ciò ha consentito di ottenere la parte cloud con solo una frazione del costo originale. Invece di aggiungere cloud alla risoluzione completa, dipingiamo solo 1/64 dei pixel e risteniamo la trama alla risoluzione completa.

![Sinistra, con scalabilità da 1/8 alla risoluzione completa; e a destra, con 3 upscale con potenza di 2.](images/stars-upscaled-300px.jpg)

Sinistra, con scalabilità da 1/8 alla risoluzione completa; e a destra, con 3 upscale con potenza di 2.


Si noti che il tentativo di passare da 1/64 delle dimensioni alla dimensione completa in un'unica operazione avrebbe un aspetto completamente diverso, perché la scheda grafica userebbe comunque 4 pixel nella configurazione per ombreggiatura di un'area più grande e gli artefatti inizieranno a essere visualizzati.

Quindi, se si aggiungono stelle a risoluzione completa con schede più piccole, si ottiene l'intera galaxy:

![Risultato quasi finale del rendering delle galaxy con stelle a risoluzione completa](images/full-galaxy-500px.png)

Dopo aver tracciato la traccia giusta con la forma, è stato aggiunto un livello di nubi, sono stati scambiati i punti temporanei con quelli dipinti in Photoshop ed è stato aggiunto un colore aggiuntivo. Il risultato è stato un'immagine di Milky Way Galaxy per cui i nostri team di progettazione e grafica hanno avuto grande distorsi e hanno soddisfatto gli obiettivi di profondità, volume e movimento, il tutto senza dover impossessarsi della CPU.

![L'ultima galaxy di Milky Way in 3D.](images/final-galaxy-500px.jpg)

L'ultima galaxy di Milky Way in 3D.


### <a name="more-to-explore"></a>Altre informazioni da esplorare

Il codice per l'app Galaxy Explorer è stato reso [](https://github.com/Microsoft/GalaxyExplorer) disponibile in GitHub per gli sviluppatori.

Per altre informazioni sul processo di sviluppo per Galaxy Explorer, Vedere tutti gli aggiornamenti del progetto precedenti nel [Microsoft HoloLens youtube.](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> è un software engineer e un appassionato di oggetti visivi. È stato l'ingegnere della grafica per Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits è</b> un art lead e un appassionato di spazio che ha gestito il team di modellazione 3D per Galaxy Explorer e ha lottato per un numero ancora maggiore di particelle.</td>
</tr>
</table>


## <a name="see-also"></a>Vedi anche
* [Galaxy Explorer in GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Aggiornamenti del progetto Galaxy Explorer su YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)