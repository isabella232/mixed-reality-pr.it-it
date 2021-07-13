---
title: Che cos'è un ologramma?
description: HoloLens consente di visualizzare e interagire con ologrammi tridimensionali, oggetti fatti di luce e suono che appaiono nel mondo che ti circonda.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, ologrammi, progettazione, interazione, visore VR di realtà mista, visore VR windows di realtà mista, che cos'è la realtà aumentata
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634332"
---
# <a name="what-is-a-hologram"></a>Che cos'è un ologramma?

HoloLens consente di visualizzare **gli ologrammi**, che sono oggetti di luce e suono che appaiono nel mondo intorno all'utente come oggetti reali. Ologrammi possibile rispondere a sguardo [fisso,](../design/gaze-and-commit.md) [movimenti](../design/gaze-and-commit.md#composite-gestures)e [comandi vocali](../design/voice-input.md). Possono anche interagire con [le superfici reali intorno](../design/spatial-mapping.md) all'utente. Ologrammi sono oggetti digitali che fanno parte del mondo.

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

## <a name="a-hologram-is-made-of-light-and-sound"></a>Un ologramma è costituito da luce e suono

### <a name="light"></a>Chiaro

Gli ologrammi HoloLens [visualizzati](../develop/platform-capabilities-and-apis/rendering.md) vengono visualizzati nella cornice olografica direttamente davanti agli occhi degli utenti. Ologrammi aggiungere luce al mondo, il che significa che è possibile vedere sia la luce dal display che la luce dal mondo circostante. Poiché HoloLens usa uno schermo additivo che aggiunge luce, il colore nero verrà reso trasparente. 

Ologrammi possono avere aspetti e comportamenti molto diversi. Alcuni sono realistici e solidi e altri sono di tipo ethereale ed ethereale. È possibile usare gli ologrammi per evidenziare le funzionalità nell'ambiente o usarle come elementi nell'interfaccia utente dell'app.

![Mani che manipolano un ologramma](images/hologram-hands-940px.jpg)

### <a name="sound"></a>Suoni

Ologrammi può anche produrre [suoni](../design/spatial-sound.md), che sembrano derivare da una posizione specifica nell'ambiente. A HoloLens, il suono proviene da due altoparlanti che si trovano direttamente sopra la propria casa. Come i display olografici, gli altoparlanti sono additivi, introducendo nuovi suoni senza bloccare i suoni dell'ambiente.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Un ologramma può essere inserito nel mondo o tag insieme all'utente

Quando si ha una posizione fissa per un ologramma, è [possibile](../design/coordinate-systems.md) posizionarlo esattamente in quel punto del mondo. L'ologramma appare stazionaria in base al mondo che ti circonda, proprio come un oggetto fisico. Se usi un [ancoraggio nello](../design/coordinate-systems.md#spatial-anchors) spazio per bloccare l'oggetto, il sistema può anche ricordare dove l'hai lasciato quando torni in seguito.

![Due uomini che usano il layout di Microsoft Dynamics 365 in uno spazio di vendita al dettaglio](images/HLS19_retailLayoutHologram_001-940px.jpg)

Alcuni ologrammi seguono invece l'utente. Si posizionano in base all'utente. È possibile scegliere di portare con se un ologramma e quindi posizionarlo sulla pareti quando si arriva a un'altra stanza.

**Procedure consigliate**

* Alcuni scenari richiedono che gli ologrammi rimangano facilmente individuabili o visibili in tutta l'esperienza. Esistono due approcci generali a questo tipo di posizionamento. Verranno ora chiamate e **bloccate per la** visualizzazione **e bloccate dal corpo.**
   * **Il contenuto visualizzato** bloccato è bloccato sul dispositivo di visualizzazione. Questo tipo di contenuto è difficile per diversi motivi, tra cui una impressione innaturale di "clingyness" che rende molti utenti frustranti e vogliono "scrollarlo di dosso". In generale, i progettisti hanno trovato migliore per evitare il blocco della visualizzazione del contenuto.
   * **Il contenuto bloccato** dal corpo può essere molto più pervaso. Il blocco del corpo si verifica quando si esegue il tethering di un ologramma al corpo o al vettore di sguardo fisso dell'utente nello spazio 3D. Molte esperienze hanno adottato un comportamento di blocco del corpo in cui l'ologramma segue lo sguardo dell'utente, che consente all'utente di ruotare il corpo e spostarsi nello spazio senza perdere l'ologramma. L'incorporamento di un ritardo consente ai movimenti dell'ologramma di essere più naturali. Ad esempio, un'interfaccia utente di base del sistema operativo Windows Holographic usa una variazione nel blocco del corpo che segue lo sguardo dell'utente con un ritardo di tipo elastico mentre l'utente ruota la testa.
* Posizionare l'ologramma a una distanza di visualizzazione comoda in genere a circa 1-2 metri dalla testa.
* Consentire agli elementi di deviare se devono essere continuamente nella cornice olografica oppure provare a spostare il contenuto su un lato dello schermo quando l'utente cambia punto di vista. Per altre informazioni, vedere [l'artilce di](../design/billboarding-and-tag-along.md) creazione di tag e di tag.

**Posizionare gli ologrammi nella zona ottimale, tra 1,25 m e 5 m**

Due metri è la distanza di visualizzazione ottimale. L'esperienza inizierà a peggiorare man appena si avvicina di più di 1 contatore. A distanze inferiori a 1 metro, gli ologrammi che si spostano regolarmente in profondità hanno maggiori probabilità di essere problematici rispetto agli ologrammi stazionari. È consigliabile ritagliare o dissolvere normalmente il contenuto quando si avvicina troppo, in modo da non creare un'esperienza di visualizzazione disgraziata per l'utente.

![Distanza ottimale per il posizionamento degli ologrammi dall'utente.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Un ologramma interagisce con l'utente e il mondo

Ologrammi non riguardano solo la luce e il suono. sono anche una parte attiva del mondo. Sguardo fisso su un ologramma e movimento con la mano e un ologramma può iniziare a seguire l'utente. Assegnare un comando vocale e l'ologramma può rispondere.

![Gruppo di operatori pubblici che usano Microsoft HoloLens 2 per collaborare a un progetto di sviluppo di una centrale eolica](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Ologrammi le interazioni personali che non sono possibili altrove. Poiché il HoloLens sa dove si trova nel mondo, un carattere olografico può guardarti direttamente negli occhi e avviare una conversazione con te.

Un ologramma può anche interagire con l'ambiente circostante. Ad esempio, è possibile posizionare una palla di gioco olografica sopra un tavolo. Quindi, con un [tocco d'aria,](../design/gaze-and-commit.md#composite-gestures)osservare il tocco della palla e fare rumore quando raggiunge il tavolo.

Ologrammi possono essere occluse anche da oggetti reali. Ad esempio, un carattere olografico potrebbe passare attraverso una porta e dietro una barriera, fuori dalla vista.

**Suggerimenti per l'integrazione di ologrammi e il mondo reale**

* L'allineamento alle regole gravitazionali rende gli ologrammi più facili da correlare e più facilmente leggibili. Ad esempio: posizionare un cane olografico a terra & un gatto sul tavolo invece di metterlo nello spazio.
* Molti progettisti hanno scoperto di poter integrare ologrammi più facilmente leggibili creando un'"ombreggiatura negativa" sulla superficie su cui si trova l'ologramma. A tale scopo, creano un alone debole sul terreno intorno all'ologramma e quindi sottraggono l'ombreggiatura dall'alone. L'alone si integra con la luce del mondo reale. L'ombreggiatura viene usata per macinare l'ologramma nell'ambiente.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>Un ologramma è ciò che <br>you can dream up<br>
        Gli sviluppatori olografici hanno la potenza di interrompere la creatività degli schermi 2D e del mondo che ti circonda.<br><br>
        Che cosa *verrà* compilato?
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Mondo immaginario olografico nel living](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Prossima stazione di scoperta

Si sta esplorando il [percorso di](get-started-with-mr.md) individuazione che abbiamo strutturato ed esplorando le nozioni di base della realtà mista. Da qui è possibile continuare con l'argomento di base successivo: 

> [!div class="nextstepaction"]
> [Espandere il processo di progettazione](case-study-expanding-the-design-process-for-mixed-reality.md)