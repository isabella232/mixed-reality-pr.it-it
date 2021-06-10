---
title: Colore, luce e materiali
description: La progettazione di contenuti per la realtà mista richiede un'attenta considerazione del colore, dell'illuminazione e dei materiali per tutti gli asset visivi.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, progettazione, colore, luce, materiali, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 2e1626e72d49107c2a83bf1123b306d3ee5c8640
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600360"
---
# <a name="color-light-and-materials"></a>Colore, luce e materiali

![Colore, luce e materiali](images/RemoteRendering.jpg)

La progettazione di contenuti per la realtà mista richiede un'attenta considerazione del colore, dell'illuminazione e dei materiali per tutti gli asset virtuali. Gli scopi dell'acustica possono includere l'uso di luce e materiale per impostare il tono di un ambiente immersivo, mentre gli scopi funzionali possono includere l'uso di colori accattivanti per avvisare gli utenti di un'azione imminente. Ognuna di queste decisioni deve essere ponderata rispetto alle opportunità e ai vincoli del dispositivo di destinazione dell'esperienza.

Di seguito sono riportate le linee guida specifiche per il rendering degli asset nei visori VR immersive e olografici. Molte di queste sono strettamente collegate ad altre aree tecniche e [](color-light-and-materials.md#see-also) un elenco di argomenti correlati è disponibile nella sezione Vedere anche alla fine di questo articolo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Rendering su dispositivi immersive e olografici

Il contenuto di cui viene eseguito il rendering in visori VR immersive apparirà visivamente diverso rispetto al contenuto sottoposto a rendering in visori VR olografici. Mentre i visori VR immersive in genere eseguono il rendering del contenuto come previsto su uno schermo 2D, i visori VR olografici come HoloLens usano schermi RGB see-through a colori per eseguire il rendering degli ologrammi.

È sempre necessario tempo per testare le esperienze olografiche in un visore VR olografico. L'aspetto del contenuto, anche se è stato creato in modo specifico per i dispositivi olografici, sarà diverso come si può vedere nei monitor secondari, negli snapshot e in una visualizzazione inevasa. Ricordarsi di fare un'esperienza con un dispositivo, testando l'illuminazione degli ologrammi e osservando da tutti i lati (oltre che dall'alto e dal basso) il rendering del contenuto. Assicurarsi di eseguire il test con una gamma di impostazioni di luminosità nel dispositivo. È improbabile che tutti gli utenti condicheranno un'impostazione predefinita presunta e un set eterogeneo di condizioni di illuminazione.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Nozioni fondamentali sul rendering nei dispositivi olografici

* **I dispositivi olografici** hanno schermi additivi: gli ologrammi vengono creati aggiungendo luce alla luce del mondo reale. Il bianco apparirà chiaro, mentre il nero apparirà trasparente.

* **L'impatto sui colori varia in base all'ambiente dell'utente:** esistono molte condizioni di illuminazione diverse nella stanza dell'utente. Creare contenuti con livelli di contrasto appropriati per maggiore chiarezza.

* **Evitare l'illuminazione** dinamica: gli ologrammi con illuminazione uniforme nelle esperienze olografiche sono i più efficienti. Usando l'illuminazione avanzata, l'illuminazione dinamica supererà probabilmente le funzionalità dei dispositivi mobili. Quando è necessaria l'illuminazione dinamica, è consigliabile usare lo [shader Mixed Reality Toolkit Standard.](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 

## <a name="designing-with-color"></a>Progettazione con colore

A causa della natura degli schermi additivi, alcuni colori possono apparire diversi nei display olografici. Alcuni colori verranno visualizzati negli ambienti di illuminazione, mentre altri verranno visualizzati come meno a impatto. I colori cool tendono a passare allo sfondo, mentre i colori ad accesso caldo passano in primo piano. Prendere in considerazione questi fattori durante l'esplorazione del colore nelle esperienze:

* **Rendering dei colori chiari:** il bianco appare chiaro e deve essere usato con modertà. Nella maggior parte dei casi, si consideri un valore bianco intorno a R 235 G 235 B 235. Aree grandi e luminosi possono causare disagi per l'utente. Per il backplate della finestra dell'interfaccia utente, è consigliabile usare colori scuri.

* **Rendering dei colori scuri:** a causa della natura degli schermi additivi, i colori scuri appaiono trasparenti. Un oggetto nero a tinta unita non apparirà diverso dal mondo reale. Vedere canale alfa più avanti. Per dare l'aspetto di "nero", provare un valore RGB grigio molto scuro, ad esempio 16,16,16.

* **Uniformità dei colori:** in genere il rendering degli ologrammi viene eseguito in modo sufficientemente chiaro in modo che mantengano l'uniformità dei colori, indipendentemente dal colore di sfondo. Le aree di grandi dimensioni possono diventare grandi. Evitare aree di grandi dimensioni di colore chiaro e a tinta unita.

* **Gamut:** HoloLens trae vantaggio da una "vasta gamma" di colori, concettualmente simile ad Adobe RGB. Di conseguenza, alcuni colori possono mostrare qualità e rappresentazione diverse nel dispositivo.

* **Gamma:** la luminosità e il contrasto dell'immagine sottoposta a rendering variano tra dispositivi immersive e olografici. Queste differenze dei dispositivi spesso sembrano rendere più o meno luminosi le aree di colore e ombreggiature più o meno scuri.

* **Separazione** dei colori: detta anche "color breakup" o "color fring", la separazione dei colori si verifica più comunemente con gli ologrammi mobili (incluso il cursore) quando un utente tiene traccia degli oggetti con gli occhi.

## <a name="technical-considerations"></a>Considerazioni tecniche

* **Aliasing:** considerare l'aliasing, i passaggi frastagliati o "scale" in cui il bordo della geometria di un ologramma incontra il mondo reale. L'uso di trame con dettagli elevati può peggiorare questo effetto. Le trame devono essere mappate e i filtri devono essere abilitati. È consigliabile sfalsare i bordi degli ologrammi o aggiungere una trama che crea un bordo nero intorno agli oggetti. Evitare la geometria sottile laddove possibile.

* **Canale alfa:** è necessario cancellare il canale alfa in modo che sia completamente trasparente per tutte le parti in cui non si esegue il rendering di un ologramma. Lasciare il valore alfa indefinito comporta artefatti visivi durante la creazione di immagini/video dal dispositivo o con la visualizzazione di controllo delle immagini.

* **Attenuazione della trama:** poiché la luce è additiva negli schermi olografici, è meglio evitare aree di grandi dimensioni di colore a tinta unita, perché spesso non producono l'effetto visivo previsto.

## <a name="design-guidelines-for-holographic-display"></a>Linee guida di progettazione per la visualizzazione olografica

![Occlusione di colore e mano](images/color_handocclusion.jpg)

Quando si progetta contenuto per schermi olografici, è necessario considerare diversi elementi per ottenere un'esperienza ottimale. Per [le linee guida e le raccomandazioni, vedere](designing-content-for-holographic-display.md) Progettazione di contenuti per la visualizzazione olografica.

## <a name="storytelling-with-light-and-color"></a>Storie con luce e colore

La luce e il colore consentono di visualizzare gli ologrammi in modo più naturale nell'ambiente dell'utente e offrono indicazioni e supporto per l'utente. Per le esperienze olografiche, considerare questi fattori durante l'esplorazione dell'illuminazione e del colore:

:::row:::
    :::column:::
* **Incisa:** un effetto di "concisa" per i materiali più scuri può aiutare a concentrare l'attenzione dell'utente sul centro del campo di visualizzazione. Questo effetto scurisce il materiale dell'ologramma in un raggio dal vettore di sguardo fisso dell'utente. Ciò è efficace anche quando l'utente visualizza gli ologrammi da un angolo obliqua o di vista.

* **Enfasi:** consente di attirare l'attenzione su oggetti o punti di interazione contrapposto a colori, luminosità e illuminazione. Per un'analisi più dettagliata dei metodi di illuminazione nella narrazione, vedere [PixelTatography - A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Immagine: uso del colore per mostrare l'enfasi per gli elementi di narrazione, mostrati qui in una scena da [Frammenti.](https://www.microsoft.com/p/fragments/9nblggh5ggm8)*
    :::column-end:::
        :::column:::
        ![Uso del colore per mostrare l'enfasi per gli elementi di narrazione, mostrati qui in una scena da Frammenti.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>Materiali

:::row:::
    :::column:::
I materiali sono elementi fondamentali per creare ologrammi realistici. Fornendo caratteristiche visive appropriate, è possibile creare oggetti olografici accattivanti che possono integrarsi bene con l'ambiente fisico. I materiali sono importanti anche per fornire feedback visivo per i vari tipi di interazioni di input dell'utente.  

[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity) uno shader MRTK Standard con varie opzioni di effetto visivo che possono essere usate per il feedback visivo. Ad esempio, è possibile usare la proprietà "Luce di prossimità" per fornire un effetto di illuminazione quando il dito dell'utente si avvicina alla superficie dell'oggetto. Altre informazioni sullo [shader MRTK Standard](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)
    :::column-end:::
        :::column:::
    *Ciclo video: esempio di feedback visivo basato sulla prossimità di un rettangolo di selezione* 
     ![ Feedback visivo sulla prossimità manuale](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>Vedi anche
* [Progettazione di contenuto per la visualizzazione olografica](designing-content-for-holographic-display.md)
* [Separazione dei colori](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [Ologrammi](../discover/hologram.md)
* [Linguaggio di progettazione Microsoft - Colore](https://www.microsoft.com/design/color)
* [piattaforma UWP (Universal Windows Platform) : colore](/windows/uwp/style/color)