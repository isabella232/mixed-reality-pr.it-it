---
title: Case study - Uso del piano di stabilizzazione
description: Scoprire in che modo il team di sviluppo ha usato il piano di stabilizzazione per ridurre la turbolenza olografica in un'applicazione di realtà mista.
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, ologrammi, stabilizzazione, case study, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale
ms.openlocfilehash: 4227be39c18e43ad712a14dd61217994a8fc761f41f9416b95b511be5396712a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202364"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Case study - Uso del piano di stabilizzazione per ridurre la turbolenza olografica

L'uso degli ologrammi è spesso difficile. Spostarsi in uno spazio e guardare gli ologrammi da tutte le diverse angolazioni offre un livello di coinvolgimento che non è disponibile sullo schermo di un normale computer. Mantenere questi ologrammi e avere un aspetto realistico è una funzionalità tecnica eseguita sia dall'hardware Microsoft HoloLens che dalla progettazione intelligente delle app olografiche.

## <a name="the-tech"></a>La tecnologia

Per fare in modo che gli ologrammi vengano visualizzati come se condividevano effettivamente lo spazio con l'utente, il rendering dovrebbe essere eseguito correttamente senza separazione dei colori. Questo risultato viene ottenuto, in parte, dalla tecnologia incorporata nell'hardware HoloLens, che mantiene gli ologrammi ancorati a quello che viene chiamato piano [di stabilizzazione.](hologram-stability.md#reprojection)

Un piano è definito da un punto e da una normale. Poiché si vuole che il piano si faccia sempre fronte alla fotocamera, è importante impostare il punto del piano. È possibile indicare HoloLens punto su cui concentrare l'elaborazione per mantenere tutti gli elementi ancorati e stabili. Tuttavia, l'impostazione di questo punto di interesse è specifica dell'app e può rendere o interrompere l'app a seconda del contenuto.

Ologrammi funziona meglio quando il piano di stabilizzazione viene applicato correttamente, ma ciò che effettivamente significa dipende dal tipo di applicazione che si sta creando. Di seguito viene illustrato in che modo alcune delle app attualmente disponibili per HoloLens risolvere questo problema.

## <a name="behind-the-scenes"></a>Dietro le quinte

Durante lo sviluppo delle app seguenti, abbiamo notato che, quando non si usava il piano, gli oggetti si muoverebbero quando la testa si spostava. Si può anche vedere la separazione dei colori con movimenti rapidi della testa o dell'ologramma. Alla fine è stato appreso come usare al meglio il piano di stabilizzazione e progettare le app in base ai problemi che non è possibile risolvere.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: contenuti stazionari, interattività 3D

[Galaxy Explorer](../unity/galaxy-explorer.md) include due elementi principali nella scena: la visualizzazione principale del contenuto celestiale e la piccola barra degli strumenti dell'interfaccia utente che segue lo sguardo fisso. Per la logica di stabilizzazione, viene illustrato l'oggetto con cui si interseca il vettore di sguardo fisso corrente in ogni fotogramma per determinare se raggiunge qualsiasi elemento in un livello di collisione specificato. In questo caso, i livelli a cui si è interessati sono i pianeta, quindi se lo sguardo cade su un pianeta, il piano di stabilizzazione viene posizionato in tale posizione. Se nessuno degli oggetti nel livello di collisione di destinazione viene raggiunto, l'app usa un livello secondario "piano B". Se non viene fisso nulla, il piano di stabilizzazione viene mantenuto alla stessa distanza di quando si osserva il contenuto. Gli strumenti dell'interfaccia utente vengono ospersi come destinazione del piano, perché il passaggio da vicino a quello di gran lunga riduce la stabilità della scena complessiva.

La progettazione di Galaxy Explorer si presta bene per mantenere le cose stabili e ridurre l'effetto della separazione dei colori. L'utente è invitato a spostarsi e aggirare il contenuto invece di spostarsi da un lato all'altro e i planeti si spostano abbastanza lentamente da non notare la separazione dei colori. Viene inoltre mantenuta una costante di 60 FPS, che impedisce la separazione dei colori.

Per verificarlo, cercare un file denominato LSRPlaneModifier.cs nel codice [di Galaxy Explorer in GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: Contenuto zionario con stato attivo dell'interfaccia utente

In HoloStudio si dedica la maggior parte del tempo a guardare lo stesso modello su cui si sta lavorando. Lo sguardo fisso non si sposta in modo significativo, tranne quando si seleziona un nuovo strumento o si vuole esplorare l'interfaccia utente, quindi è possibile mantenere semplice la logica di impostazione del piano. Quando si esamina l'interfaccia utente, il piano è impostato su qualsiasi elemento dell'interfaccia utente a cui si blocca lo sguardo fisso. Quando si esamina il modello, il piano è a una distanza impostata, corrispondente alla distanza predefinita tra l'utente e il modello.

![Il piano di stabilizzazione visualizzato in HoloStudio quando l'utente guarda il pulsante Home](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour e Visualizzatore 3D: contenuto stazionario con animazione e film

In HoloTour e Visualizzatore 3D si sta esaminando un oggetto animato o un film animato solitario con effetti 3D aggiunti sopra di esso. La stabilizzazione in queste app è impostata su qualsiasi elemento attualmente visualizzato.

HoloTour impedisce anche di allontanarsi troppo dal mondo virtuale facendo in modo che si sposti con l'utente invece di rimanere in una posizione fissa. In questo modo si garantisce che gli altri ologrammi non siano abbastanza distorsi dagli altri ologrammi per evitare problemi di stabilità.

![In questo esempio di HoloTour, il piano di stabilizzazione verrebbe impostato su questo film di Pantheon di Hadrian.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: Contenuto dinamico e interazioni ambientali

Impostare il piano di stabilizzazione in RoboRaid è sorprendentemente semplice, nonostante sia l'app che richiede il movimento più improvviso. Il piano è orientato verso il fissarsi delle pareti o degli oggetti circostante e fluttua a una distanza fissa davanti a te quando sei abbastanza lontano.

RoboRaid è stato progettato in base al piano di stabilizzazione. Il reticolo, che si sposta maggiormente dal momento che è bloccato con la testa, elude questo problema usando solo il rosso e il blu, riducendo al minimo qualsiasi colorazione. Contiene anche un piccolo bit di profondità tra le parti, riducendo al minimo qualsiasi colore smarramento che si verificherebbe mascherando l'elemento con un effetto parallasse già previsto. I robot non si spostano rapidamente e si spostano solo a brevi distanze a intervalli regolari. Tendono a rimanere di fronte a circa 2 metri, dove la stabilizzazione è impostata per impostazione predefinita.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Frammenti e young conker: contenuto dinamico con interazione ambientale

Scritto da Asobo Studio in C++, Fragments e Young Conker hanno un approccio diverso per impostare il piano di stabilizzazione. I punti di interesse vengono definiti nel codice e ordinati in base alla priorità. Gli elementi poI sono contenuti in gioco, ad esempio il modello Conker in Young Conker, i menu, il reticolo di puntamento e i logo. Gli oggetti poI vengono intersecati dallo sguardo dell'utente e il piano viene impostato sul centro dell'oggetto con la priorità più alta. Se non si verifica alcuna intersezione, il piano viene impostato sulla distanza predefinita.

Frammenti e Young Conker progettano anche intorno a te che devi allontanarti troppo dagli ologrammi sosendo l'app se ti sposti al di fuori di ciò che è stato analizzato in precedenza come spazio di riproduzione. Di conseguenza, consentono di mantenere l'utente entro i limiti trovati per offrire l'esperienza più stabile.

## <a name="do-it-yourself"></a>Provare

Se si ha una HoloLens e si vogliono provare i concetti descritti in questo articolo, è possibile scaricare una scena di test per provare gli esercizi seguenti. La scena di test usa l'API gizmo incorporata di Unity per visualizzare la posizione in cui viene impostato il piano. Il codice è stato usato anche per acquisire gli screenshot in questo case study.
1. Sincronizzare la versione più [recente di MixedRealityToolkit-Unity.](https://github.com/Microsoft/MixedRealityToolkit-Unity)
2. Aprire la [scena HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity.](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)
3. Compilare e configurare il progetto generato.
4. Eseguire nel dispositivo.

### <a name="exercise-1"></a>Esercizio 1

Verranno visualizzati diversi puntini bianchi intorno a diversi orientamenti. Davanti a te verranno visualizzati tre punti a diverse profondità. Tocco dell'aria per modificare il punto su cui è impostato il piano. Per questo esercizio e per gli altri due, spostarsi nello spazio mentre si guardano i punti. Ruotare la testa verso sinistra, destra, verso l'alto e verso il basso. Spostarsi più vicino e più lontano dai punti. Vedere come reagiscono quando il piano di stabilizzazione è impostato su obiettivi diversi.

### <a name="exercise-2"></a>Esercizio 2

A questo punto, ruotare verso destra fino a visualizzare due punti in movimento, uno che ruota su un tracciato orizzontale e uno su un tracciato verticale. Ancora una volta, eseguire il tocco per modificare il punto su cui è impostato il piano. Si noti che la separazione dei colori è attenuata e viene visualizzata sul punto connesso al piano. Toccare di nuovo per usare la velocità del punto nella funzione di impostazione del piano. Questo parametro fornisce un suggerimento per HoloLens sul movimento previsto dell'oggetto. È importante sapere quando usare questa opzione, come si noterà quando si usa la velocità su un punto, l'altro punto mobile mostrerà una maggiore separazione dei colori. Tenere presente questo problema quando si progettano le app: la presenza di un flusso coeso al movimento degli oggetti può contribuire a impedire la visualizzazione degli artefatti.

### <a name="exercise-3"></a>Esercizio 3

Tornare a destra ancora una volta finché non viene visualizzata una nuova configurazione di punti. In questo caso, sono presenti punti nella distanza e un punto che si allontana da essi. Tocco dell'aria per modificare il punto su cui è impostato il piano, alternando i punti nella parte posteriore e il punto in movimento. Si noti come l'impostazione della posizione del piano e della velocità su quella del punto a forma di puntino fa sì che gli artefatti vengano visualizzati ovunque.

**Suggerimenti**
* Mantenere semplice la logica di impostazione del piano. Come si è visto, non sono necessari algoritmi di impostazione del piano complessi per creare un'esperienza immersiva. Il piano di stabilizzazione è solo una parte del rompicapo.
* Quando possibile, spostare sempre il piano tra destinazioni senza problemi. Il passaggio immediato di destinazioni distanti può interrompere visivamente la scena.
* È consigliabile avere un'opzione nel piano che imposta la logica per bloccare una destinazione specifica. In questo modo, è possibile fare in modo che il piano sia bloccato su un oggetto, ad esempio un logo o una schermata del titolo, se necessario.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>Software Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche
* [Nozioni di base MR 100: Introduzione a Unity](../unity/tutorials/holograms-100.md)
* [Punto focale in Unity](../unity/focus-point-in-unity.md)
* [Stabilità degli ologrammi](hologram-stability.md)
