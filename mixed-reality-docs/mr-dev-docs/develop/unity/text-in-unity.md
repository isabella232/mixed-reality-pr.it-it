---
title: Testo in Unity
description: "Per visualizzare il testo in Unity, è possibile usare due tipi di componenti di testo: testo dell'interfaccia utente e mesh di testo 3D."
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, progettazione, controlli, tipo di carattere, tipografia, interfaccia utente, esperienza utente, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, MRTK, realtà mista Toolkit
ms.openlocfilehash: 3e5f296e9526e62bde7d03a0fee7847f4664e4a67187fcda1e66e22aa03053b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207937"
---
# <a name="text-in-unity"></a>Testo in Unity

Il testo è uno dei componenti più importanti nelle app olografiche. Per visualizzare il testo in Unity, è possibile usare tre tipi di componenti di testo: testo dell'interfaccia utente, mesh di testo 3D e mesh Pro. Per impostazione predefinita, il testo dell'interfaccia utente e la mesh testo 3D appaiono sfocati e sono troppo grandi. La modifica di alcune variabili comporta un testo più nitido e di qualità superiore con dimensioni gestibili in HoloLens. È possibile ottenere una qualità di rendering migliore applicando un fattore di ridimensionamento per ottenere dimensioni appropriate quando si usano i componenti Testo dell'interfaccia utente e Mesh testo 3D.

![Come ottenere testo nitido e ben fatto](images/hug-text-02-640px.png)<br>
*Testo predefinito sfocato in Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Uso del testo 3D di Unity (mesh di testo) e del testo dell'interfaccia utente

Unity presuppone che tutti i nuovi elementi aggiunti a una scena siano di dimensioni un'unità Unity o una scala di trasformazione al 100%. Un'unità Unity si traduce in circa 1 contatore HoloLens. Per i tipi di carattere, il rettangolo di selezione per un textmesh 3D è disponibile per impostazione predefinita a circa 1 metro di altezza.

![Uso dei tipi di carattere in Unity](images/640px-hug-text-03.png)<br>
*Il testo 3D unity predefinito (mesh di testo) occupa un'unità Unity, ovvero 1 contatore*

<br>

La maggior parte delle finestre di progettazione visiva usa i punti per definire le dimensioni dei caratteri nel mondo reale. Sono presenti circa 2835 punti (2.834.645666399962) in 1 contatore. In base alla conversione del sistema di punti in 1 contatore e alle dimensioni del carattere di Mesh testo predefinite di Unity pari a 13, la semplice matematica di 13 divisa per 2835 è uguale a 0,0046 (0,004586111116 per l'esattezza) che offre una scala standard buona da cui iniziare (alcuni potrebbero voler arrotondare a 0,005). Il ridimensionamento dell'oggetto di testo o del contenitore a questi valori non solo consente la conversione 1:1 delle dimensioni dei caratteri in un programma di progettazione, ma fornisce anche uno standard che consente di mantenere la coerenza nell'intera esperienza.

![Valori di ridimensionamento per il testo 3D e il testo dell'interfaccia utente di Unity](images/Text_In_Unity_Measurements1.png)<br>
*Valori di ridimensionamento per il testo 3D e il testo dell'interfaccia utente di Unity*

<br>

![Mesh di testo 3D unity con valori ottimizzati](images/hug-text-05-1000px.png)<br>
*Mesh di testo 3D unity con valori ottimizzati*

<br>

Quando si aggiunge un elemento di testo basato su un'interfaccia utente o un'area di disegno a una scena, la disparità di dimensioni è ancora maggiore. Le differenze nelle due dimensioni sono pari a circa il 1000%, che porterebbe il fattore di scala per i componenti di testo basati sull'interfaccia utente a 0,00046 (0,000458611116 per l'esatta) o 0,00005 per il valore arrotondato.

![Testo dell'interfaccia utente di Unity con valori ottimizzati](images/hug-text-04-1000px.png)<br>
*Testo dell'interfaccia utente di Unity con valori ottimizzati*

<br>

>[!NOTE]
>Il valore predefinito di qualsiasi tipo di carattere può essere influenzato dalla dimensione della trama del tipo di carattere o dalla modalità di importazione del tipo di carattere in Unity. Questi test sono stati eseguiti in base al tipo di carattere Arial predefinito in Unity e a un altro tipo di carattere importato.

## <a name="working-with-text-mesh-pro"></a>Uso della mesh di testo Pro

Con La mesh di testo di Unity Pro, è possibile proteggere la qualità del rendering del testo. Supporta i contorni di testo nitidi indipendentemente dalla distanza usando la tecnica [SDF (Signed Distance](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) Field). Usando lo stesso metodo di calcolo usato in precedenza per la mesh di testo 3D e il testo dell'interfaccia utente, è possibile trovare i valori di ridimensionamento appropriati da usare con i punti tipografici convenzionali. Poiché il tipo di carattere 3D Text Mesh Pro predefinito con dimensioni pari a 36 ha una dimensione di delimitazione di 2,5 unità Unity (2,5 m), è possibile usare un valore di ridimensionamento pari a 0,005 per ottenere la dimensione del punto. La mesh di Pro nel menu dell'interfaccia utente ha una dimensione di delimitazione predefinita di 25 unità Unity (25 m). In questo modo viene restituito 0,0005 per il valore di ridimensionamento.

![Ridimensionamento dei valori per il testo e l'interfaccia utente 3D di Unity](images/Text_In_Unity_Measurements2.png)<br>
*Ridimensionamento dei valori per il testo e l'interfaccia utente 3D di Unity*

## <a name="recommended-text-size"></a>Dimensioni del testo consigliate

Come puoi aspettarti, le dimensioni dei tipi usate in un PC o in un tablet (in genere tra 12 e 32 pt) hanno un aspetto ridotto a una distanza di 2 metri. Dipende dalle caratteristiche di ogni tipo di carattere, ma in generale l'angolo di visualizzazione minimo consigliato e l'altezza del carattere per la leggibilità sono di circa 0,35°-0,4°/12,21-13,97 mm in base agli studi di ricerca degli utenti. Si tratta di circa 35-40 pt con il fattore di scala introdotto in precedenza.

Per l'interazione da vicino a 0,45 m (45 cm), l'angolo di visualizzazione minimo del tipo di carattere leggibile e l'altezza sono 0,4°-0,5° / 3,14–3,9 mm. Si tratta di circa 9-12 pt con il fattore di scala introdotto in precedenza.

![Intervallo di interazione da vicino e da ](images/typography-distance-1000px.jpg)
 *lontano Contenuto nell'intervallo di interazione da vicino e da lontano*

### <a name="the-minimum-legible-font-size"></a>Dimensioni minime leggibili del carattere

| Distanza | Angolo di visualizzazione | Altezza del testo | Dimensioni del carattere |
|---------|---------|---------|---------|
| 45 cm (distanza di manipolazione diretta) | 0.4°-0.5° | 3,14–3,9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>Dimensioni del carattere leggibili e leggibili

| Distanza | Angolo di visualizzazione | Altezza del testo | Dimensioni del carattere |
|---------|---------|---------|---------|
| 45 cm (distanza di manipolazione diretta) | 0.65°-0.8° | 5,1-6,3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20,9-26,2 mm | 59.4-74.2 pt |

Segoe UI (il tipo di carattere predefinito per Windows) funziona bene nella maggior parte dei casi. Tuttavia, evitare di usare famiglie di caratteri leggere o semi-leggere di piccole dimensioni, perché i tratti verticali leggeri vibrano e peggiorano la leggibilità. I tipi di carattere moderni con spessore del tratto sufficiente funzionano correttamente. Helvetica e Arial, ad esempio, sono leggibili in modo HoloLens con pesi normali o in grassetto.

![Visualizzazione della ](images/Text_In_Unity_ViewingAngle.jpg)
 *distanza, dell'angolo e dell'altezza del testo di visualizzazione dell'angolo*

## <a name="text-with-mixed-reality-toolkit-v2"></a>Testo con realtà mista Toolkit v2

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Qualità del rendering del testo acuto con dimensioni appropriate

In base a questi fattori di ridimensionamento, sono stati creati prefab di testo con [testo dell'interfaccia utente e mesh di testo 3D.](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text) Gli sviluppatori possono usare questi prefab per ottenere testo acuto e dimensioni del carattere coerenti.

![Qualità del rendering del testo acuto con dimensioni appropriate](images/hug-text-06-1000px.png)<br>
*Qualità del rendering del testo acuto con dimensioni appropriate*

### <a name="shader-with-occlusion-support"></a>Shader con supporto dell'occlusione

Il materiale del tipo di carattere predefinito di Unity non supporta l'occlusione. Per questo problema, per impostazione predefinita verrà visualizzato il testo dietro gli oggetti. È stato incluso un semplice [shader che supporta l'occlusione](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader). L'immagine seguente mostra il testo con materiale del tipo di carattere predefinito (a sinistra) e il testo con occlusione appropriata (a destra).

![Shader con supporto dell'occlusione](images/hug-text-07-1000px.png)<br>
*Shader con supporto dell'occlusione*

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando i blocchi predefiniti principali di MRTK. Da qui, è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Input vocale](voice-input-in-unity.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Prefab di testo in MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [Tipografia](../../design/typography.md)
