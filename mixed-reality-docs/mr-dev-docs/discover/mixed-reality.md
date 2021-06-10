---
title: Realtà mista?
description: Discussione sulla realtà mista, demomstrating dell'uso di dispositivi AR e VR nello spettro della realtà mista.
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: Realtà mista, olografica, AR, VR, MR, XR, realtà aumentata, realtà virtuale, spiegazione, case study, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, che cos'è la realtà virtuale, che cos'è la realtà aumentata
ms.localizationpriority: high
ms.openlocfilehash: 0ff9fcd79c778c2b056cd0c6035ddf8cb005273a
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547114"
---
# <a name="what-is-mixed-reality"></a>Che cos'è Realtà mista?

![Puntamento e commit con le mani in HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

La realtà mista è una fusione tra mondo fisico e mondo digitale che rende possibili nuove interazioni tra uomo, computer e ambiente. Questa nuova realtà è il frutto dei progressi compiuti nei settori della visione artificiale, dell'elaborazione grafica, della tecnologia di visualizzazione e dei sistemi di input. Il termine *realtà mista*, tuttavia, è stato coniato nel 1994 in un documento a cura di Paul Milgram e Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)" (Tassonomia dei dispositivi di visualizzazione nella realtà mista). Questo documento ha preso il esame il concetto di *continuum di virtualizzazione* e la categorizzazione della tassonomia applicata ai dispositivi di visualizzazione. Da quel momento in poi, l'applicazione della realtà mista è andata oltre i dispositivi di visualizzazione per includere:
* Input ambientale
* Audio spaziale
* Posizioni e posizionamento negli spazi reali e virtuali

![Immagine dello spettro della realtà mista](images/mixedrealityspectrum-worlds.png)<br>
*Immagine: la realtà mista è il risultato della fusione del mondo fisico con il mondo digitale.*

<br>

---

## <a name="environmental-input-and-perception"></a>Input e percezione ambientali

Negli ultimi decenni è stata approfondita sempre di più la relazione tra input umano e del computer, portando a un disciplina nota come *interazione uomo-computer* o HCI L'input umano avviene attraverso diversi mezzi, tra cui tastiere, mouse, tocco, input penna, voce e anche il tracciamento dello scheletro con Kinect.

I miglioramenti apportati ai sensori e all'elaborazione stanno creando nuove aree di input computer dagli ambienti. L'interazione tra computer e ambienti è una conoscenza o *percezione* ambientale ed è proprio per questo motivo che le API di Windows che rivelano informazioni ambientali sono chiamate [API di percezione](/uwp/api/Windows.Perception). L'input ambientale acquisisce elementi come la posizione di una persona nell'ambiente ([tracciamento del movimento della testa](../design/coordinate-systems.md)), le superfici e i confini ([mapping spaziale](../design/spatial-mapping.md) e [conoscenza della scena](../design/scene-understanding.md)), l'illuminazione ambientale, l'audio ambientale, il riconoscimento degli oggetti e la posizione.

<br>

![Diagramma di Venn che mostra le interazioni tra computer, persone e ambienti](images/mixed-reality-venn-diagram-300px.png)<br> 
*Immagine: interazioni tra computer, persone e ambienti.*

<br>

La combinazione di questi tre elementi, **elaborazione del computer, input umano e input ambientale**, consente di creare vere esperienze di realtà mista. Il movimento nel mondo fisico si traduce in movimento nel mondo digitale. I confini nel mondo fisico influenzano le esperienze delle applicazioni, ad esempio le esperienze di gioco, nel mondo digitale. Senza l'input ambientale, non è possibile fondere le esperienze tra realtà fisiche e digitali.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Spettro della realtà mista

Dal momento che la realtà mista è una combinazione tra mondo fisico e mondo digitale, queste due realtà definiscono i poli estremi di uno spettro noto come continuum di virtualizzazione. La gamma delle realtà è denominata *spettro della realtà mista*. Sul lato sinistro è presente la realtà fisica in cui si trova l'uomo. Sul lato destro è presente la realtà digitale corrispondente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realtà aumentata e realtà virtuale

La maggior parte dei telefoni cellulari attualmente presenti sul mercato non dispone di alcuna capacità di conoscenza ambientale. Le esperienze che offrono non possono combinare realtà fisiche e digitali. Le esperienze di sovrapposizione di grafica sui flussi video del mondo fisico costituiscono la *realtà aumentata*. Le esperienze che occludono la vista per presentare un'esperienza digitale costituiscono la *realtà virtuale*. Le esperienze possibili tra la realtà aumentata e la realtà virtuale costituiscono la *realtà mista*:
* Iniziando dal mondo fisico, si inserisce un oggetto digitale, ad esempio un ologramma, come se fosse presente.
* Partendo dal mondo fisico, una rappresentazione digitale di un'altra persona, un avatar, mostra la posizione in cui si trovava quando ha lasciato gli appunti. In altre parole, queste sono esperienze che rappresentano la collaborazione asincrona in momenti diversi.
* Partendo da un mondo digitale, i confini fisici del mondo fisico, ad esempio i muri e i mobili, vengono visualizzati digitalmente all'interno dell'esperienza per aiutare gli utenti a evitare gli oggetti fisici.

<br>

![Spettro della realtà mista](images/mixedrealityspectrum.png)<br>
*Immagine: spettro della realtà mista*

<br>

Nella maggior parte dei casi, le offerte di realtà aumentata e realtà virtuale attualmente disponibili rappresentano una piccola parte di questo spettro e sono considerate sottoinsiemi dello spettro della realtà mista complessivo. Windows 10 è stato creato tenendo conto dell'intero spettro e consente di combinare rappresentazioni digitali di persone, luoghi e cose con il mondo reale.


## <a name="devices-and-experiences"></a>Dispositivi ed esperienze

Esistono due tipi principali di dispositivi che offrono esperienze Windows Mixed Reality:
1. I **dispositivi olografici** sono caratterizzati dalla capacità del dispositivo di collocare contenuti digitali nel mondo reale come se vi si trovassero effettivamente.
2. I **dispositivi immersive** sono caratterizzati dalla capacità del dispositivo di creare un senso di "presenza", nascondendo il mondo fisico e sostituendolo con un'esperienza digitale.

<table>
<tr>
<th width="30%"> Caratteristica</th><th width="35%"> Dispositivi olografici</th><th width="35%"> Dispositivi immersive</th>
</tr><tr>
<td><strong>Dispositivo di esempio</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Schermo</strong></td><td> Display trasparente. Consente all'utente di vedere l'ambiente fisico mentre indossa il visore VR.</td><td> Display opaco. Blocca la vista dell'ambiente fisico mentre si indossa il visore VR.</td>
</tr><tr>
<td><strong>Movement</strong></td><td> Movimento di sei gradi di libertà, con rotazione e traslazione.</td><td> Movimento di sei gradi di libertà, con rotazione e traslazione.</td>
</tr>
</table> 


> [!NOTE]
> Il fatto che un dispositivo sia connesso, anche con tethering, a un PC separato (tramite cavo USB o Wi-Fi) o che sia un dispositivo autonomo (senza tethering) non indica se si tratta di un dispositivo olografico o immersive. Le funzionalità che migliorano la mobilità determinano una migliore esperienza e i dispositivi olografici e immersive possono essere sia con che senza tethering.

Il progresso tecnologico rende possibili esperienze di realtà mista, ma non sono disponibili al momento dispositivi in grado di offrire esperienze che coprono l'intero spettro. Windows 10 offre una piattaforma di realtà mista comune per produttori e sviluppatori di dispositivi. I dispositivi odierni possono supportare una gamma specifica nell'ambito dello spettro della realtà mista e tale gamma si arricchirà con nuovi dispositivi. In futuro i dispositivi olografici saranno più immersive e i dispositivi immersive saranno più olografici.

<br>

![Tipi di dispositivi nello spettro della realtà mista](images/Final_WhatIsMixedReality07.png)<br>
*Immagine: posizione occupata dai dispositivi nello spettro della realtà mista*

È preferibile pensare al tipo di esperienza che uno sviluppatore di applicazioni o giochi vuole creare. Le esperienze in genere indicano un punto o una parte specifica dello spettro. Gli sviluppatori devono valutare le capacità dei dispositivi a cui mirare. Le esperienze che si basano sul mondo fisico verranno eseguite in modo ottimale in HoloLens.
* **Verso sinistra (in prossimità della realtà fisica).** Gli utenti rimangono presenti nell'ambiente fisico e non hanno mai l'impressione di aver lasciato tale ambiente.
* **Al centro (completamente nella realtà mista).** Queste esperienze fondono il mondo reale e il mondo digitale. Chi ha visto il film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) può riconciliare il modo in cui la struttura fisica della casa in cui si è svolta la trama è stata fusa con una giungla.
* **Verso destra (in prossimità della realtà digitale).** Gli utenti sperimentano un ambiente digitale e non sono consapevoli di ciò che accade nell'ambiente fisico che li circonda.

## <a name="next-discovery-checkpoint"></a>Prossima stazione di scoperta

Se si sta seguendo il [percorso di scoperta](get-started-with-mr.md) definito, è possibile esplorare le nozioni di base della realtà mista. Da qui è possibile continuare con l'argomento di base successivo: 

> [!div class="nextstepaction"]
> [Che cos'è un ologramma?](hologram.md)
