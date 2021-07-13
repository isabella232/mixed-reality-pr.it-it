---
title: Che cos'è Realtà mista?
description: Discussione sulla realtà mista, demomstrating dell'uso di dispositivi AR e VR nello spettro della realtà mista.
author: qianw211
ms.author: v-qianwen
ms.date: 07/01/2021
ms.topic: article
keywords: Realtà mista, olografica, AR, VR, MR, XR, realtà aumentata, realtà virtuale, spiegazione, case study, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, che cos'è la realtà virtuale, che cos'è la realtà aumentata
ms.localizationpriority: high
ms.openlocfilehash: 088bc9a978bd236069ddc1beab40387c607b906e
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634322"
---
# <a name="what-is-mixed-reality"></a>Che cos'è Realtà mista?

La realtà mista è l'onda successiva nell'elaborazione seguita da mainframe, PC e smartphone. La realtà mista è sempre più importante per i consumatori e le aziende.  Ci libera dalle esperienze associate a schermo, offrendo interazioni istintiva con i dati negli spazi di vita, tra le cose e con gli amici.  Gli esploratori online, in centinaia di milioni in tutto il mondo, hanno riscontrato la realtà mista tramite i dispositivi portatili.  Ar per dispositivi mobili offre oggi le soluzioni di realtà mista più mainstream sui social media. Le persone potrebbero non rendersi conto che i filtri AR che usano in Reality sono esperienze di realtà mista.  Microsoft Mixed Reality porta tutte queste esperienze utente al livello successivo con una combinazione di rappresentazioni olografiche davvero straordinarie di persone, modelli 3D olografici ad alta fedeltà e il mondo reale che le circonda.

![Puntamento e commit con le mani in HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

La realtà mista è una combinazione di mondo fisico e digitale, che sblocca interazioni 3D naturali e intuitive con esseri umani, computer e ambiente. Questa nuova realtà si basa su miglioramenti della visione informatica, dell'elaborazione grafica, delle tecnologie di visualizzazione, dei sistemi di input e cloud computing. Il termine Realtà mista è stato introdotto in un documento del 1994 di Paul Milgram e Fumio Kishino,["A Taxonomy of Mixed Reality Visual Displays".](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321) Il documento ha esplorato il concetto di *continuità* virtuale e la tassonomia degli schermi visivi. Da quel momento in poi, l'applicazione della realtà mista è andata oltre i dispositivi di visualizzazione per includere:

* Comprensione dell'ambiente: mapping spaziale e ancoraggi.
* Comprensione umana: tracciamento delle mani, tracciamento oculare e input vocale.
* Audio spaziale.
* Posizioni e posizionamento in spazi fisici e virtuali.
* Collaborazione su asset 3D in spazi di realtà mista.

![Immagine dello spettro della realtà mista](images/mixedrealityspectrum-worlds.png)<br>
*Immagine: la realtà mista è il risultato della fusione del mondo fisico con il mondo digitale.*

<br>

---

## <a name="environmental-input-and-perception"></a>Input e percezione ambientali

Negli ultimi decenni, la relazione tra esseri umani e computer ha continuato a evolversi con i metodi di input.  È emersa una nuova disciplina, nota come interazione umana-computer o HCI. L'input umano può ora includere tastiere, mouse, tocco, input penna, voce e Kinect rilevamento dello scheletro.

I miglioramenti dei sensori e della potenza di elaborazione stanno creando nuove percezioni di ambienti basati su metodi di input avanzati. Ecco perché i nomi delle API in Windows che rivelano informazioni ambientali sono chiamati [API di percezione.](/uwp/api/Windows.Perception) Gli input ambientali possono acquisire: 

* posizione del corpo di una persona nel mondo fisico[(tracciamento della testa)](../design/coordinate-systems.md) 
* oggetti, superfici e limiti[(mapping spaziale e](../design/spatial-mapping.md) comprensione [della scena)](../design/scene-understanding.md) 
* illuminazione ambientale e audio
* riconoscimento di oggetti
* posizioni fisiche

<br>

![Diagramma di Venn che mostra le interazioni tra computer, persone e ambienti](images/mixed-reality-venn-diagram-300px.png)<br> 
*Immagine: interazioni tra computer, persone e ambienti.*

<br>

Una combinazione dei tre elementi essenziali consente di creare esperienze di realtà mista vere:

* Elaborazione di computer basata sul cloud
* Metodi di input avanzati
* Percezioni ambientali

Mentre ci si sposta nel mondo fisico, i movimenti vengono mappati in una realtà digitale. I limiti fisici influenzano le esperienze di realtà mista nel mondo digitale, ad esempio giochi o linee guida basate su attività in un impianto di produzione. Con l'input ambientale e le percezioni, le esperienze iniziano a confondersi tra realtà fisiche e digitali.

<br>

---

## <a name="the-mixed-reality-spectrum"></a>Spettro della realtà mista

La realtà mista unisce sia il mondo fisico che quello digitale.  Queste due realtà contrassegnano le estremità polari di uno spettro noto come *continuità virtuale.* Si fa riferimento a questo spettro di realtà come spettro *di realtà mista.*  Alla fine dello spettro si ha la realtà fisica che si ha come esseri umani. Dall'altra parte dello spettro, è disponibile la realtà digitale corrispondente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realtà aumentata e realtà virtuale

La maggior parte dei telefoni cellulari sul mercato oggi non ha capacità di percezione ambientale limitate o nessuna. Le esperienze offerte da questi telefoni non possono combinare realtà fisiche e digitali. 

Le esperienze che sovrapporno grafica, flussi video o ologrammi nel mondo fisico sono chiamate realtà aumentata. Le esperienze che occludono la visualizzazione per presentare un'esperienza digitale completamente immersiva sono la realtà virtuale. Le esperienze che possono passare tra realtà aumentata e virtuale formano realtà mista, in cui è possibile:

* Posizionare un oggetto digitale, ad esempio un ologramma, nel mondo fisico, come se fosse fisicamente presente.
* Essere personalmente e digitalmente presenti nel mondo fisico, sotto forma di avatar, per collaborare in modo asincrono con altri utenti in punti diversi nel tempo.
* Nella realtà virtuale, i limiti fisici, ad esempio le pareti e i mobili, appaiono digitalmente all'interno dell'esperienza per consentire agli utenti di evitare ostacoli fisici.

<br>

![Spettro della realtà mista](images/mixedrealityspectrum.png)<br>
*Immagine: spettro della realtà mista*

<br>

La maggior parte delle esperienze di realtà aumentata e realtà virtuale attualmente disponibili rappresenta un piccolo subset dello spettro più ampio della realtà mista. Windows 10 è stato creato tenendo conto dell'intero spettro e consente di combinare rappresentazioni digitali di persone, luoghi e cose con il mondo reale.

## <a name="devices-and-experiences"></a>Dispositivi ed esperienze

Esistono due tipi principali di dispositivi che offrono esperienze Windows Mixed Reality:
1. I **dispositivi olografici** sono caratterizzati dalla capacità del dispositivo di collocare contenuti digitali nel mondo reale come se vi si trovassero effettivamente.
2. **I dispositivi VR immersive** sono caratterizzati dalla capacità del dispositivo di creare un senso di presenza bloccando il mondo fisico e sostituendolo con un'esperienza digitale completamente immersiva.

<table>
<tr>
<th width="30%"> Caratteristica</th><th width="35%"> Dispositivi olografici</th><th width="35%"> Dispositivi immersive</th>
</tr><tr>
<td><strong>Dispositivo di esempio</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Schermo</strong></td><td> Display trasparente. Consente all'utente di visualizzare l'ambiente fisico mentre si indossa il visore VR.</td><td> Display opaco. Blocca la vista dell'ambiente fisico mentre si indossa il visore VR.</td>
</tr><tr>
<td><strong>Movement</strong></td><td> Movimento di sei gradi di libertà, con rotazione e traslazione.</td><td> Movimento di sei gradi di libertà, con rotazione e traslazione.</td>
</tr>
</table> 

> [!NOTE]
> Il fatto che un dispositivo sia con tethering in un PC separato (tramite cavo USB o Wi-Fi) o senza tethering non riflette se un dispositivo è olografico o immersive. Le funzionalità che migliorano la mobilità offrono spesso esperienze migliori. I dispositivi olografici e immersive possono essere con tethering o senza tethering.

Le esperienze di realtà mista sono il risultato di miglioramenti tecnologici. Attualmente non sono presenti dispositivi in grado di eseguire esperienze nell'intero spettro. Windows 10 offre una piattaforma di realtà mista comune per produttori e sviluppatori di dispositivi. Qualsiasi dispositivo attualmente in uso può supportare un intervallo specifico all'interno dello spettro della realtà mista. In futuro sono previsti nuovi dispositivi con una gamma più ampia: i dispositivi olografici saranno più immersive e i dispositivi immersive saranno più olografici.

<br>

![Tipi di dispositivi nello spettro della realtà mista](images/Final_WhatIsMixedReality07.png)<br>
*Immagine: posizione occupata dai dispositivi nello spettro della realtà mista*

Quale tipo di esperienze si vuole creare per gli sviluppatori di applicazioni o giochi? Le esperienze in genere indicano un punto o una parte specifica dello spettro. È necessario prendere in considerazione le funzionalità dei dispositivi di destinazione. Le esperienze che si basano sul mondo fisico verranno eseguite in modo ottimale in HoloLens.

* **Verso sinistra (in prossimità della realtà fisica).** Gli utenti rimangono presenti nella loro realtà fisica e non sono in grado di ritiene di aver lasciato tale realtà.
* **Al centro (completamente nella realtà mista).** Queste esperienze fondono il mondo reale e il mondo digitale. Nel film [Jumanji,](https://en.wikipedia.org/wiki/Jumanji)ad esempio, la struttura fisica della casa in cui è stata raccontata la storia è stata mista a un ambiente di gioco.
* **Verso destra (in prossimità della realtà digitale).** Gli utenti sperimentano una realtà digitale e non sono a conoscenza della realtà fisica che li circonda.

## <a name="next-discovery-checkpoint"></a>Prossima stazione di scoperta

Sei all'inizio del [](get-started-with-mr.md) percorso di individuazione che abbiamo stabilito per te ed esplora le nozioni di base della realtà mista. Da qui è possibile continuare con l'argomento di base successivo: 

> [!div class="nextstepaction"]
> [Che cos'è un ologramma?](hologram.md)
