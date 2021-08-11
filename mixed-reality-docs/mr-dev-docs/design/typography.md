---
title: Tipografia
description: Informazioni su come progettare e implementare il testo come elemento importante per la distribuzione di informazioni nell'esperienza dell'app di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, progettazione, stile, carattere, tipografia, interfaccia utente, ux, testo, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens
ms.openlocfilehash: 7df2386f3478c0b0b79d198a3342bc9a9a061f6e5a305baedcd91be9c2f09f04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200286"
---
# <a name="typography"></a>Tipografia

![Esempio di tipografia in HoloLens](images/typography-cover.png)<br>


Il testo è un elemento importante per fornire informazioni nell'esperienza dell'app. Proprio come per la tipografia su schermi 2D, l'obiettivo è chiarezza e leggibilità. Con l'aspetto tridimensionale della realtà mista, è possibile influire ancora di più sul testo e sull'esperienza utente complessiva.

Quando si parla di tipo in 3D, si tende a pensare a testo 3D estruso e volumetrico. Ad eccezione di alcune progettazioni logotype e di altre applicazioni limitate, il testo estruso tende a ridurre la leggibilità del testo. Anche se si progettano esperienze per la 3D, si usa 2D per il tipo perché è più leggibile e più facile da leggere.

In HoloLens tipo viene costruito con ologrammi usando la luce basata sul sistema di colore additivo. Analogamente ad altri ologrammi, il tipo può essere inserito nell'ambiente effettivo in cui può essere bloccato e osservato da qualsiasi angolazione. Anche [l'effetto parallassa](https://en.wikipedia.org/wiki/Parallax) tra il tipo e l'ambiente aggiunge profondità all'esperienza.

## <a name="typography-in-mixed-reality"></a>Tipografia nella realtà mista

Le regole tipografiche nella realtà mista non sono diverse da altre. Il testo sia nel mondo fisico che nel mondo virtuale deve essere leggibile e leggibile. Il testo può essere su una parete o sovrapposto a un oggetto fisico. Potrebbe essere mobile insieme a un'interfaccia utente digitale. Indipendentemente dal contesto, vengono applicate le stesse regole tipografiche per la lettura e il riconoscimento.

### <a name="create-clear-hierarchy"></a>Creare una gerarchia chiara

Creare contrasti e gerarchie usando diverse dimensioni e pesi dei tipi. La definizione di una rampa di tipo e il suo seguito in tutta l'esperienza dell'app offriranno un'esperienza utente ottimale con una gerarchia di informazioni coerente.

![Esempi di rampa di tipi](images/typography-ramp-1000px.jpg)<br>
*Definire la rampa di tipi e seguirla in tutta l'esperienza dell'app*

### <a name="limit-your-fonts"></a>Limitare i tipi di carattere

Evitare di usare più di due diverse famiglie di caratteri in un unico contesto. Troppi tipi di carattere interromperanno l'armoniosa e coerenza dell'esperienza e renderanno più difficile l'utilizzo delle informazioni. In HoloLens, poiché le informazioni vengono sovrapposte all'ambiente fisico, l'uso di troppi stili di carattere degraderà l'esperienza. Segoe UI è il tipo di carattere per tutti i progetti digitali Microsoft. Viene usato in modo coerente nella shell Windows Mixed Reality. È possibile scaricare il file Segoe UI tipo di carattere dalla pagina [Windows design toolkit](/windows/uwp/design-downloads/).

[Altre informazioni sul carattere Segoe UI carattere](/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evitare spessori del carattere sottili

Evitare di usare pesi del carattere chiaro o semi chiaro per le dimensioni del tipo sotto i 42 pt perché i tratti verticali sottili vibrano e degradano la leggibilità. I tipi di carattere moderni con spessore del tratto sufficiente funzionano bene. Ad esempio, Helvetica e Arial sono leggibili in HoloLens con pesi regolari o in grassetto.

### <a name="color"></a>Color

In HoloLens, poiché gli ologrammi sono costruiti con un sistema di luce additiva, il testo bianco è altamente leggibile. È possibile trovare esempi di testo bianco nel menu Start e nella barra dell'app. Anche se il testo bianco funziona correttamente senza un back plate HoloLens, uno sfondo fisico complesso potrebbe rendere il tipo difficile da leggere. È consigliabile usare il testo bianco su una lastra posteriore scura o colorata per migliorare lo stato attivo dell'utente e ridurre al minimo la distrazione da uno sfondo fisico.

<br>


![È consigliabile usare testo bianco su una lastra posteriore scura o colorata. ](images/typography-whiteonblack2-1000px.jpg)
 *Esempi di testo bianco su una lastra posteriore scura o colorata.*
<br>

Per usare testo scuro, è consigliabile usare una lastra posteriore brillante per renderlo leggibile. Nei sistemi a colori additivi il nero viene visualizzato come trasparente. Ciò significa che il testo nero non verrà visualizzato senza una barra posteriore colorata.

:::row:::
    :::column:::
        ![Esempi di bianco su nero e nero su testo bianco](images/typography-whiteonblack.png)<br>
        *Esempi di bianco su nero e nero su testo bianco*<br>
    :::column-end:::
    :::column:::
        ![Esempi di testo nero nelle app di sistema - Store e Impostazioni](images/640px-typography-blackonwhite.jpg)<br>
        *Esempi di testo nero nelle app di sistema - Store e Impostazioni*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>Dimensioni del carattere consigliate

Come ci si può aspettare, le dimensioni dei tipi usate in un PC o in un dispositivo tablet (in genere tra 12 e 32 pt) sono piccole a una distanza di 2 metri. Dipende dalle caratteristiche di ogni tipo di carattere, ma in generale l'angolo di visualizzazione minimo consigliato e l'altezza del carattere per la leggibilità sono di circa 0,35°-0,4°/12,21-13,97 mm in base agli studi di ricerca degli utenti. Si tratta di circa 35-40 pt con il fattore di scala introdotto nella [pagina Testo in Unity.](../develop/unity/text-in-unity.md) 

Per l'interazione vicina a 0,45 m(45 cm), l'angolo di visualizzazione minimo del tipo di carattere leggibile e l'altezza sono 0,4°-0,5° / 3,14–3,9 mm. Si tratta di circa 9-12 pt con il fattore di scala introdotto in [Text in Unity.](../develop/unity/text-in-unity.md)

![Intervallo di interazione vicino e lontano ](images/typography-distance-1000px.jpg)
 *Contenuto nell'intervallo di interazione* vicino e lontano

### <a name="the-minimum-legible-font-size"></a>Dimensione minima del carattere leggibile

| Distanza | Angolo di visualizzazione | Altezza del testo | Dimensioni carattere** |
|---------|---------|---------|---------|
| 45 cm (distanza di manipolazione diretta) | 0.4°-0.5° | Da 3,14 a 3,9 mm | 8.9-11.13pt |
| 2 m | 0.35°-0.4° | 12.21-13.97mm | 34.63-39.58 pt |

### <a name="the-comfortably-legible-font-size"></a>Dimensioni del carattere facilmente leggibili

| Distanza | Angolo di visualizzazione | Altezza del testo | Dimensioni carattere** |
|---------|---------|---------|---------|
| 45 cm (distanza di manipolazione diretta) | 0.65°-0.8° | 5,1-6,3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20,9-26,2 mm | 59.4-74.2 pt |


Segoe UI (il tipo di carattere predefinito per Windows) funziona correttamente nella maggior parte dei casi. Evitare di usare famiglie di caratteri chiaro o semi chiaro di piccole dimensioni perché i tratti verticali sottili vibrano e degradano la leggibilità. I tipi di carattere moderni con spessore del tratto sufficiente funzionano bene. Ad esempio, Helvetica e Arial hanno un aspetto straordinario e sono leggibili in HoloLens con pesi regolari o in grassetto.

**Per informazioni più dettagliate sul calcolo delle dimensioni del testo in Unity, vedere [Text in Unity (Testo in Unity)](../develop/unity/text-in-unity.md)**

![Visualizzazione della ](images/Text_In_Unity_ViewingAngle.jpg)
 *distanza, dell'angolo e dell'altezza del testo di visualizzazione*

<br>

---

## <a name="resources"></a>Risorse

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Tipi di carattere Segoe](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (file ZIP)<br>
    ### <a name="hololens-fontbr"></a>[HoloLens carattere](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (file ZIP)<br>
    <br>
    *Immagine: il HoloLens tipo di carattere fornisce i glifi dei simboli usati Windows Mixed Reality.*
    :::column-end:::
        :::column:::
        ![Il HoloLens tipo di carattere fornisce i glifi dei simboli usati in Windows Mixed Reality](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>Vedi anche

* [Testo in Unity](../develop/unity/text-in-unity.md)
* [Colore, luce e materiali](./color-light-and-materials.md)