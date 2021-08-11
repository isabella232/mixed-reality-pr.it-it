---
title: Che cos'è un ologramma?
description: HoloLens consente di visualizzare e interagire con ologrammi tridimensionali, oggetti fatti di luce e suono che appaiono nel mondo intorno a te.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, ologrammi, progettazione, interazione, visore di realtà mista, visore windows mixed reality, che cos'è la realtà aumentata
ms.openlocfilehash: e028fe6180bded26263fa47feb5acefc94570222e43f10fe85db5adf90307844
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202116"
---
# <a name="what-is-a-hologram"></a>Che cos'è un ologramma?

HoloLens consente di visualizzare **gli ologrammi**, che sono oggetti fatti di luce e suono che appaiono nel mondo intorno a te come oggetti reali. Ologrammi possibile rispondere agli [](../design/gaze-and-commit.md)sguardi, [ai movimenti](../design/gaze-and-commit.md#composite-gestures)e ai [comandi vocali.](../design/voice-input.md) Possono anche interagire con [le superfici reali intorno](../design/spatial-mapping.md) a te. Ologrammi sono oggetti digitali che fanno parte del mondo.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

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
        <td>Holograms (Ologrammi)</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>Un ologramma è fatto di luce e suono

### <a name="light"></a>Chiaro

Gli ologrammi HoloLens [rendering](../develop/platform-capabilities-and-apis/rendering.md) vengono visualizzati nel frame olografico direttamente davanti agli occhi degli utenti. Ologrammi aggiungere luce al mondo, il che significa che si vede sia la luce dal display che la luce dal mondo circostante. Poiché HoloLens usa uno schermo additivo che aggiunge luce, il colore nero verrà reso trasparente. 

Ologrammi possono avere aspetti e comportamenti molto diversi. Alcune sono realistiche e solide, altre sono da fumetto ed eteree. È possibile usare gli ologrammi per evidenziare le funzionalità nell'ambiente o usarle come elementi nell'interfaccia utente dell'app.

![Mani che manipolano un ologramma](images/hologram-hands-940px.jpg)

### <a name="sound"></a>Suoni

Ologrammi può anche produrre [suoni](../design/spatial-sound.md), che sembrano provengono da una posizione specifica nell'ambiente. In HoloLens, il suono proviene da due altoparlanti che si trovano direttamente sopra le orecchini. Come i display olografici, gli altoparlanti sono additivi, introducendo nuovi suoni senza bloccare i suoni dall'ambiente.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Un ologramma può essere inserito nel mondo o tag insieme all'utente

Quando si ha una posizione fissa per un ologramma, è [possibile](../design/coordinate-systems.md) posizionarlo esattamente in quel punto del mondo. Mentre si va in giro, l'ologramma appare stazionario in base al mondo intorno a te, proprio come un oggetto fisico. Se si usa un [ancoraggio spaziale](../design/coordinate-systems.md#spatial-anchors) per bloccare l'oggetto, il sistema può anche ricordare dove è stato lasciato quando si torna in un secondo momento.

![Due uomini che usano il layout di Microsoft Dynamics 365 in uno spazio di vendita al dettaglio](images/HLS19_retailLayoutHologram_001-940px.jpg)

Alcuni ologrammi seguono invece l'utente. Si posizionano in base all'utente. È possibile scegliere di portare con se un ologramma e quindi posizionarlo sulla parete quando si arriva in un'altra stanza.

**Procedure consigliate**

* Alcuni scenari richiedono che gli ologrammi rimangano facilmente individuabili o visibili in tutta l'esperienza. Esistono due approcci generali a questo tipo di posizionamento. Verranno ora chiamate **display-locked** e **body-locked**.
   * **Il contenuto bloccato** dalla visualizzazione è bloccato sul dispositivo di visualizzazione. Questo tipo di contenuto è difficile per diversi motivi, tra cui un senso innaturale di "agitazione" che rende molti utenti frustrati e vogliono "scrollarlo di dosso". In generale, i progettisti hanno trovato meglio evitare il contenuto di blocco della visualizzazione.
   * **Il contenuto bloccato** dal corpo può essere molto più perdonante. Il blocco del corpo si verifica quando si esegue il tethering di un ologramma al corpo dell'utente o al vettore di sguardo nello spazio 3D. Molte esperienze hanno adottato un comportamento di blocco del corpo in cui l'ologramma segue lo sguardo dell'utente, che consente all'utente di ruotare il corpo e spostarsi nello spazio senza perdere l'ologramma. L'incorporamento di un ritardo consente ai movimenti dell'ologramma di essere più naturali. Ad esempio, un'interfaccia utente principale del sistema operativo Windows Holographic usa una variazione nel blocco del corpo che segue lo sguardo dell'utente con un leggero ritardo elastico mentre l'utente volta la testa.
* Posizionare l'ologramma a una distanza di visualizzazione comoda in genere a circa 1-2 metri dalla testa.
* Consentire la deriva degli elementi se devono essere continuamente nel frame olografico o prendere in considerazione lo spostamento del contenuto su un lato dello schermo quando l'utente cambia il proprio punto di vista. Per altre informazioni, vedere l'artilce di creazione di tag e di creazione di [tag.](../design/billboarding-and-tag-along.md)

**Posizionare gli ologrammi nella zona ottimale, tra 1,25 e 5 m**

Due metri è la distanza di visualizzazione ottimale. L'esperienza inizierà a peggiorare quando si avvicina più di 1 metro. A distanze inferiori a 1 metro, gli ologrammi che si spostano regolarmente in profondità hanno maggiori probabilità di essere problematici rispetto agli ologrammi stazionari. È consigliabile ritagliare o dissolvere normalmente il contenuto quando si avvicina troppo, in modo da non creare un'esperienza di visualizzazione spiacevole per l'utente.

![Distanza ottimale per il posizionamento di ologrammi dall'utente.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Un ologramma interagisce con l'utente e il mondo

Ologrammi non si tratta solo di luce e suono; sono anche una parte attiva del mondo. Osservare un ologramma e un movimento con la mano e un ologramma può iniziare a seguirti. Assegnare un comando vocale e l'ologramma può rispondere.

![Gruppo di operatori pubblici che usano Microsoft HoloLens 2 per collaborare a un progetto di sviluppo di un'azienda eolica](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Ologrammi le interazioni personali che non sono possibili altrove. Poiché l HoloLens sa dove si trova nel mondo, un carattere olografico può guardarti direttamente negli occhi e iniziare una conversazione con te.

Un ologramma può anche interagire con l'ambiente circostante. Ad esempio, è possibile posizionare una palla di rimbalzo olografica sopra una tabella. Quindi, con un [tocco d'aria,](../design/gaze-and-commit.md#composite-gestures)osservare il rimbalzo della palla e fare rumore mentre raggiunge il tavolo.

Ologrammi possono anche essere occluded da oggetti reali. Ad esempio, un carattere olografico potrebbe passare attraverso una porta e dietro una parete, fuori dalla vista.

**Suggerimenti per l'integrazione degli ologrammi e del mondo reale**

* L'allineamento alle regole gravitazionali rende gli ologrammi più facili da correlare e da rendere più leggibili. Ad esempio: posizionare un cane olografico a terra & un vasino sul tavolo invece di fluttuare nello spazio.
* Molti progettisti hanno scoperto di poter integrare ologrammi più riconoscibili creando un'"ombreggiatura negativa" sulla superficie su cui si trova l'ologramma. A tale scopo, creano un bagliore leggero sul terreno intorno all'ologramma e quindi sottraendo l'"ombreggiatura" dal bagliore. Il bagliore leggero si integra con la luce del mondo reale. L'ombreggiatura viene usata per a terra l'ologramma nell'ambiente.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>Un ologramma è ciò che <br>è possibile realizzare<br>
        Gli sviluppatori olografici hanno il potere di interrompere la creatività da schermi 2D e nel mondo che ti circonda.<br><br>
        Cosa *si compila?*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Mondo immaginario olografico in living](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Prossima stazione di scoperta

Si sta esplorando il percorso [di](get-started-with-mr.md) individuazione che è stato descritto ed esplorando le nozioni di base della realtà mista. Da qui è possibile continuare con l'argomento di base successivo: 

> [!div class="nextstepaction"]
> [Espandere il processo di progettazione](case-study-expanding-the-design-process-for-mixed-reality.md)