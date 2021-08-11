---
title: Manipolazione diretta con le mani
description: Informazioni sulla manipolazione diretta, un modello di input in cui gli utenti toccano gli ologrammi direttamente con le mani.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, Sguardo fisso, selezione della destinazione con lo sguardo, interazione, progettazione, a portata di mano, HoloLens, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, MRTK, Mixed Reality Toolkit, pulsante, collisori, cubo di delimitazione, 2D, movimenti istintivi
ms.openlocfilehash: 30b7a3c343ff044595beb6dfe2b62b1c70ff5a2ff3f6dd51563018ceee2fb995
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192702"
---
# <a name="direct-manipulation-with-hands"></a>Manipolazione diretta con le mani

![Pulsante](images/UX_Hero_Manipulation.jpg)

La manipolazione diretta è un modello di input che consiste nel toccare gli ologrammi direttamente con le mani. L'idea alla base di questo concetto è che il comportamento degli oggetti deve essere uguale a quello che avrebbero nella realtà. I pulsanti possono essere attivati semplicemente premendoli, gli oggetti possono essere selezionati afferrandoli e il contenuto 2D si comporta come un touchscreen virtuale. La manipolazione diretta è basata sull'invito, ovvero è facile da usare. Non esistono movimenti simbolici da insegnare agli utenti. Tutte le interazioni avvengono intorno a un elemento visivo che è possibile toccare o afferrare. È considerata un modello di input "da vicino", in quanto è ideale per interagire con contenuto raggiungibile stendendo le braccia.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Modello di input</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
     <td><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Manipolazione diretta con le mani</td>
     <td>❌ Non supportata</td>
     <td>✔️ Consigliata</td>
     <td>➕ Supportata.  Per l'interfaccia utente, consigliamo invece <a href="point-and-commit.md">Puntamento e commit con le mani</a>.</td>
    
</tr>
</table>


La manipolazione diretta è un modello di input principale in HoloLens 2 che usa il nuovo sistema di tracciamento delle mani articolato. Il modello di input è disponibile anche su visori VR immersive tramite l'uso di controller del movimento, ma non è consigliato come mezzo principale di interazione al di fuori della manipolazione di oggetti. La manipolazione diretta non è disponibile in HoloLens (prima generazione).

<br>

---

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a>Demo di base del rilevamento delle mani e delle interazioni istintiva

Se si desidera vedere i concetti di progettazione di Head e Eye Tracking in azione, vedere la demo video Progettazione **di Ologrammi - Tracciamento** testina e tracciamento oculare di seguito. Al termine, continuare per un'analisi più dettagliata di argomenti specifici.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

*Questo video è stato tratto dall'app "Progettazione Ologrammi" HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*

## <a name="collidable-fingertip"></a>Punta del dito di collisione

In HoloLens 2 le mani dell'utente vengono riconosciute e interpretate come modelli scheletrici delle mani sinistra e destra. Per implementare l'idea di toccare gli ologrammi direttamente con le mani, in teoria si potrebbero applicare cinque collisori alle cinque punte delle dita del modello scheletrico di ogni mano. Tuttavia, a causa della mancanza di feedback tattili, 10 punte di dita di collisione possono causare collisioni inaspettate e imprevedibili con gli ologrammi. 

È consigliabile applicare solo un collisore a ogni dito indice. Le punte degli indici di collisione possono comunque fungere da punti tocco attivi per vari movimenti di tocco che coinvolgono altre dita. I movimenti di tocco includono la pressione con un dito, il tocco con un dito, la pressione con due dita e la pressione con cinque dita, come mostrato di seguito:

:::row:::
    :::column:::
       ![Punta del dito di collisione](images/Collidable-Fingertip.jpg)<br>
       **Punta del dito di collisione**<br>
    :::column-end:::
    :::column:::
       ![Pressione con un dito](images/Collidable-Fingertip-1-finger-press.jpg)<br>
        **Pressione con un dito**<br>
    :::column-end:::
    :::column:::
       ![Tocco con un dito](images/Collidable-Fingertip-1-finger-tap.jpg)<br>
       **Tocco con un dito**<br>
    :::column-end:::
    :::column:::
       ![Pressione con cinque dita](images/Collidable-Fingertip-5-finger-press.jpg)<br>
       **Pressione con cinque dita**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a>Collisore sfera

Invece di usare una forma generica casuale, è consigliabile usare un collisore sferico. È possibile quindi eseguirne il rendering visivo per fornire segnali migliori per la destinazione più vicina. Il diametro della sfera deve corrispondere allo spessore del dito indice per aumentare l'accuratezza del tocco. È più facile recuperare la variabile dello spessore di un dito chiamando l'API relativa alla mano.

### <a name="fingertip-cursor"></a>Cursore punta del dito

Oltre al rendering di una sfera di collisione sulla punta dell'indice, è stato creato un cursore avanzato per la punta del dito per migliorare l'esperienza di selezione della destinazione da vicino. Si tratta di un cursore a forma di anello associato alla punta dell'indice. In base alla prossimità, reagisce in modo dinamico a una destinazione per l'orientamento e le dimensioni come indicato di seguito:

* Quando un indice si sposta verso un ologramma, il cursore è sempre parallelo alla superficie dell'ologramma e si restringe gradualmente.
* Non appena il dito tocca la superficie, il cursore si riduce a un punto ed emette un evento tocco.

Con il feedback interattivo, gli utenti possono eseguire attività di selezione della destinazione da vicino ad alta precisione, ad esempio l'attivazione di un collegamento ipertestuale o la pressione di un pulsante, come illustrato di seguito. 

:::row:::
    :::column:::
       ![Cursore punta del dito da lontano](images/Fingertip-cursor-far.jpg)<br>
       **Cursore punta del dito da lontano**<br>
    :::column-end:::
    :::column:::
       ![Cursore punta del dito da vicino](images/Fingertip-cursor-near.jpg)<br>
        **Cursore punta del dito da vicino**<br>
    :::column-end:::
    :::column:::
       ![Cursore punta del dito con contatto](images/Fingertip-cursor-contact.jpg)<br>
       **Cursore punta del dito con contatto**<br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a>Cubo di delimitazione con shader prossimità

L'ologramma stesso richiede anche la possibilità di fornire feedback audio e video per compensare la mancanza di feedback tattili. Su questa esigenza si basa il concetto di cubo di delimitazione con shader prossimità. Un cubo di delimitazione è un'area volumetrica minima che racchiude un oggetto 3D. Il cubo di delimitazione è dotato di un meccanismo di rendering interattivo denominato shader prossimità. Comportamento dello shader prossimità:

:::row:::
    :::column:::
       ![Posizionamento del dito (da lontano) con feedback visivo](images/bounding-box-with-proximity-shader-hover-far.jpg)<br>
       **Posizionamento del dito (da lontano)**<br>
       Quando l'indice è all'interno della portata, sulla superficie del cubo di delimitazione viene messo in evidenza un punto luminoso per la punta del dito.
    :::column-end:::
    :::column:::
       ![Avvicinamento del dito con feedback visivo](images/bounding-box-with-proximity-shader-hover-near.jpg)<br>
        **Avvicinamento del dito**<br>
        Man mano che la punta del dito si avvicina alla superficie, il punto luminoso si restringe.
    :::column-end:::
    :::column:::
       ![Inizio contatto](images/bounding-box-with-proximity-shader-begin-contact.jpg)<br>
       **Inizio contatto**<br>
       Non appena la punta del dito tocca la superficie, l'intero cubo di delimitazione cambia colore o genera un effetto visivo per riflettere lo stato di tocco.
    :::column-end:::
    :::column:::
       ![Fine contatto](images/bounding-box-with-proximity-shader-end-contact.jpg)<br>
       **Fine contatto**<br>
       È anche possibile attivare un effetto sonoro per migliorare il feedback del tocco visivo.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a>Pulsante a pressione

Dotati di punta del dito di collisione, gli utenti sono ora pronti per interagire con un componente dell'interfaccia utente olografica di base, ovvero il pulsante a pressione. Un pulsante a pressione è un pulsante olografico personalizzato per la pressione diretta con un dito. Anche in questo caso, a causa della mancanza di feedback tattili, un pulsante a pressione è dotato di un paio di meccanismi per ovviare ai problemi correlati al feedback tattile.

* Il primo meccanismo è un cubo di delimitazione con shader prossimità, descritto in dettaglio nella sezione precedente. Serve per fornire un'idea più accurata di prossimità quando gli utenti si avvicinano ed entrano in contatto con un pulsante.
* Il secondo meccanismo è la depressione. La depressione crea un senso di pressione dopo che la punta di un dito entra in contatto con un pulsante. Il meccanismo funziona in modo che il pulsante si muova in stretta relazione con la pressione del dito lungo l'asse di profondità. Il pulsante può essere attivato quando raggiunge una profondità scelta (alla pressione) o quando lascia la profondità (al rilascio) dopo averla attraversata.
* È consigliabile aggiungere l'effetto audio di attivazione del pulsante per migliorare il feedback.

:::row:::
    :::column:::
       ![Pulsante a pressione (lontano)](images/pressable-button-far.jpg)<br>
       **Il dito è lontano**<br>
    :::column-end:::
    :::column:::
       ![Pulsante a pressione (vicino)](images/pressable-button-approach.jpg)<br>
        **Il dito si avvicina**<br>
    :::column-end:::
    :::column:::
       ![Inizio del contatto con il pulsante a pressione](images/pressable-button-contact.jpg)<br>
       **Inizio contatto**<br>
    :::column-end:::
    :::column:::
       ![Pressione del pulsante a pressione](images/pressable-button-press.jpg)<br>
       **Pressione in profondità**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>Interazione con uno slate 2D

Uno [slate](slate.md) 2D è un contenitore olografico usato per ospitare contenuti di app 2D, ad esempio un Web browser. Il concetto di progettazione per l'interazione con uno slate 2D tramite manipolazione diretta corrisponde all'interazione con un touchscreen fisico.

### <a name="to-interact-with-the-slate-contact"></a>Per interagire con il contatto tramite slate

:::row:::
    :::column:::
       ![Tocco](images/2d-slate-interaction-touch.jpg)<br>
       **Tocco**<br>
       Usa un indice per premere un pulsante o un collegamento ipertestuale.
    :::column-end:::
    :::column:::
       ![Scorrimento](images/2d-slate-interaction-scroll2.jpg)<br>
        **Scorrimento**<br>
        Usa un indice per scorrere il contenuto dello slate verso l'alto o verso il basso.
    :::column-end:::
    :::column:::
       ![Zoom](images/2d-slate-interaction-zoom2.jpg)<br>
       **Zoom**<br>
       L'utente usa i due indici per eseguire lo zoom avanti e indietro del contenuto dello slate in base al movimento relativo delle dita.
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a>Per manipolare lo slate 2D

:::row:::
    :::column:::
       ![Immagine che mostra la funzionalità di cattura e trascinamento](images/manipulate-2d-slate-move.jpg)<br>
       **Spostamento**<br>
       Sposta le mani verso angoli e i bordi per rivelare gli inviti di manipolazione più vicini. Afferra la barra dell'ologramma nella parte superiore dello slate 2D per spostare l'intero slate.
    :::column-end:::
    :::column:::
       ![Immagine che mostra la funzionalità di ridimensionamento](images/manipulate-2d-slate-scale.jpg)<br>
        **Ridimensionamento**<br>
        Afferrare gli inviti di manipolazione ed eseguire un ridimensionamento uniforme tramite gli inviti degli angoli.
    :::column-end:::
    :::column:::
       ![Adatta il contenuto in modo dinamico](images/manipulate-2d-slate-reflow.jpg)<br>
       **Adatta il contenuto in modo dinamico**<br>
       Afferrare gli inviti di manipolazione e adattare il contenuto dinamicamente tramite gli inviti dei bordi.
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a>Manipolazione di oggetti 3D

HoloLens 2 consente agli utenti di usare le mani per indirizzare e manipolare gli oggetti olografici 3D applicando un cubo di delimitazione a ogni oggetto 3D. Il cubo di delimitazione fornisce una migliore percezione della profondità tramite lo shader prossimità. Con il cubo di delimitazione sono disponibili due approcci di progettazione per la manipolazione di oggetti 3D.

### <a name="affordance-based-manipulation"></a>Manipolazione basata sugli inviti

Permette di manipolare l'oggetto 3D tramite un cubo di delimitazione e gli inviti di manipolazione intorno a esso. 

:::row:::
    :::column:::
       ![Immagine che mostra il cubo di delimitazione di un oggetto e la funzionalità di spostamento](images/3d-object-manipulation-move.jpg)<br>
       **Spostamento**<br>
       Nel momento in cui la mano di un utente è vicina a un oggetto 3D, diventano visibili il cubo di delimitazione e l'invito più vicino. Gli utenti possono afferrare il cubo di delimitazione per spostare l'intero oggetto.
    :::column-end:::
    :::column:::
       ![Immagine che mostra l'utente che afferra un bordo di un oggetto per eseguire la rotazione](images/3d-object-manipulation-rotate.jpg)<br>
        **Rotazione**<br>
        Gli utenti possono afferrare gli inviti dei bordi per eseguire la rotazione.
    :::column-end:::
    :::column:::
       ![Immagine che mostra l'utente che afferra un angolo di un oggetto per eseguire il ridimensionamento](images/3d-object-manipulation-scale.jpg)<br>
       **Ridimensionamento**<br>
       Gli utenti possono afferrare gli inviti degli angoli per eseguire un ridimensionamento uniforme.
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a>Manipolazione non basata sugli inviti

Con questo tipo di manipolazione, non è associato alcun invito al cubo di delimitazione. Gli utenti possono solo visualizzare il cubo di delimitazione e quindi interagire direttamente con esso. Se il cubo di delimitazione viene afferrato con una mano, lo spostamento e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano. Quando l'oggetto viene afferrato con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base al relativi movimenti delle mani.

Una manipolazione specifica richiede precisione. È consigliabile usare la **manipolazione basata sugli inviti**, poiché offre un elevato livello di granularità. Per una manipolazione flessibile, è consigliabile usare la **manipolazione non basata sugli inviti**, perché trasmette esperienze immediate e divertenti.

<br>

---


## <a name="instinctual-gestures"></a>Movimenti istintivi

Con HoloLens (prima generazione) sono stati insegnati agli utenti un paio di movimenti predefiniti, ad esempio l'apertura della mano a fiore e la simulazione del tocco. Per HoloLens 2 non viene richiesto agli utenti di memorizzare movimenti simbolici. Tutti i movimenti richiesti agli utenti per interagire con ologrammi e contenuti sono istintivi. Per ottenere il movimento istintivo è sufficiente guidare gli utenti a eseguire gesti in base a come sono progettati gli inviti dell'interfaccia utente.

Se ad esempio un oggetto o un punto di controllo deve essere afferrato avvicinando due dita, l'oggetto o il punto di controllo deve essere piccolo. Se si vuole che l'utente afferri con cinque dita, l'oggetto o il punto di controllo deve essere relativamente grande. Come avviene per i pulsanti, un pulsante piccolo consentirebbe agli utenti di eseguire la pressione con un solo dito. Un pulsante grande inviterebbe gli utenti a fare pressione con i palmi.


:::row:::
    :::column:::
       ![Figura che mostra l'utente che afferra un oggetto piccolo per eseguire lo spostamento](images/instinctual-gestures-smallobject.jpg)<br>
       **Oggetto piccolo**<br>
    :::column-end:::
    :::column:::
       ![Figura che mostra l'utente che afferra un oggetto medio per eseguire lo spostamento](images/instinctual-gestures-mediumobject.jpg)<br>
        **Oggetto medio**<br>
    :::column-end:::
    :::column:::
       ![Figura che mostra l'utente che afferra un oggetto grande per eseguire lo spostamento](images/instinctual-gestures-largeobject.jpg)<br>
       **Oggetto grande**<br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Progettazione simmetrica tra mani e controller 6DoF

Avrai notato che sono presenti simmetrie di interazione che è possibile tracciare tra le mani nella realtà aumentata (AR) e i controller del movimento nella realtà virtuale (VR). Entrambi gli input possono essere usati per avviare manipolazioni dirette nei rispettivi ambienti. In HoloLens 2 afferrare e trascinare con le mani a una distanza ravvicinata funziona praticamente come il pulsante usato per afferrare nei controller del movimento in WMR. In questo modo si offre una familiarità di interazione tra le due piattaforme che può rivelarsi utile se in futuro si decidesse di convertire l'applicazione da una piattaforma all'altra.

<br>

---

## <a name="optimize-with-eye-tracking"></a>Ottimizzare con il tracciamento oculare

La manipolazione diretta può essere fantastica se funziona come previsto. Ma può anche diventare frustrante se non riesci a spostare la mano in una direzione qualunque senza attivare involontariamente un ologramma. Il tracciamento oculare aiuta a identificare meglio l'intenzione dell'utente.

* **Quando**: per ridurre l'attivazione involontaria di una risposta di manipolazione. Il tracciamento oculare consente di comprendere meglio l'attività in cui è attualmente impegnato un utente.
Si supponga ad esempio di essere impegnati nella lettura di un testo olografico (istruzioni) e di sporgersi per afferrare uno strumento di lavoro del mondo reale.

In questo modo si sposta accidentalmente la mano su alcuni pulsanti olografici interattivi non notati prima (forse perché erano fuori del campo visivo).

Se l'utente non ha guardato un ologramma per un periodo di tempo ma è stato rilevato un evento di tocco o cattura, è probabile che l'interazione non sia intenzionale.

* **Quale**:  oltre alla gestione delle attivazioni false positive, un altro esempio include una migliore identificazione degli ologrammi da afferrare o toccare dal momento che il punto di intersezione preciso potrebbe non essere chiaro dalla tua prospettiva, soprattutto in presenza di più ologrammi ravvicinati.

  Anche se il tracciamento oculare in HoloLens 2 presenta limiti relativamente all'accuratezza di determinazione dello sguardo, questa funzionalità può comunque essere utile per le interazioni da vicino a causa della disparità di profondità durante l'interazione con l'input mano. Ciò significa che talvolta è difficile determinare se la mano si trova dietro o davanti a un ologramma, ad esempio per afferrare con precisione un widget di manipolazione.

* **Dove**: usa le informazioni su ciò che l'utente sta guardando con movimenti di lancio rapido. Afferra un ologramma e scaglialo verso la destinazione prevista.  

    Anche se questa soluzione a volte funziona correttamente, l'esecuzione rapida di movimenti della mano può avere come risultato destinazioni estremamente imprecise. Il tracciamento oculare tuttavia può migliorare l'accuratezza del movimento.

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a>Manipolazione in MRTK (Mixed Reality Toolkit) per Unity
Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile ottenere facilmente un comportamento di manipolazione comune usando lo script **ObjectManipulator**. ObjectManipulator consente di afferrare e spostare gli oggetti direttamente con le mani o con il raggio della mano. Supporta anche la manipolazione a due mani per il ridimensionamento e la rotazione di un oggetto.

* [MRTK - Manipolazione](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a>Vedere anche

* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)