---
title: Audio in realtà mista
description: L'audio in realtà mista può aumentare la fiducia degli utenti nelle interazioni con l'interfaccia utente e coinvolgere gli utenti nell'esperienza.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: suono spaziale, audio surround, audio 3D, audio spaziale, visore di realtà mista, visore windows di realtà mista, visore per realtà virtuale, HoloLens, MRTK, mixed reality Toolkit, case study, acustica
ms.openlocfilehash: 75b87098f90611140d2c43bb596e7c5d50dab9c47fc49426d5bcbbe0095c3847
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188821"
---
# <a name="audio-in-mixed-reality"></a>Audio in realtà mista

L'audio è una parte essenziale della progettazione e della produttività nella realtà mista. Il suono può:
* Aumentare l'attendibilità dell'utente nelle interazioni con movimenti e voce.
* Guida gli utenti ai passaggi successivi.
* Combinare in modo efficace gli oggetti virtuali con il mondo reale.

Il rilevamento della testa a bassa latenza dei visori di realtà mista, HoloLens, supporta la spazializzazione basata su HRTF di alta qualità. È possibile spazializzare l'audio nell'applicazione per:
* Prestare attenzione agli elementi visivi.
* Aiutare gli utenti a mantenere la consapevolezza dell'ambiente reale.

L'acustica connette in modo più profondo gli ologrammi al mondo della realtà mista. Fornisce suggerimenti sull'ambiente e sullo stato dell'oggetto.

Vedere esempi [dettagliati di progettazione che usa l'audio](spatial-sound-design.md).

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Spazializzazione</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Accelerazione hardware di spazializzazione</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>Uso dei suoni nella realtà mista

[L'uso dei suoni nella realtà](spatial-sound-design.md) mista richiede un approccio diverso rispetto alle applicazioni touch e tastiera e mouse. Le principali decisioni di progettazione del suono includono i suoni da spazializzare e le interazioni da sonificare. Queste decisioni influenzano fortemente la fiducia degli utenti, la produttività e la curva di apprendimento.

### <a name="case-studies"></a>Case study

HoloTour porta virtualmente gli utenti in siti di interesse e storici in tutto il mondo. Vedere Progettazione [del suono per HoloTour](case-study-spatial-sound-design-for-holotour.md) case study. Per acquisire gli spazi del soggetto sono stati usati un microfono speciale e una configurazione per il rendering.

RoboRaid è uno spartito ad alta energia per HoloLens. La [progettazione del suono per RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study descrive le scelte di progettazione effettuate per garantire che l'audio spaziale sia stato usato nel modo più completo.

## <a name="spatialization"></a>Spazializzazione

La spazializzazione è il componente direzionale dell'audio spaziale. Per una configurazione home theater 7.1, la spazializzazione è semplice come la panoramica tra altoparlanti. Tuttavia, per le cuffia in realtà mista, è essenziale usare una tecnologia basata su HRTF per la precisione e il comfort. Windows la spazializzazione basata su HRTF e questo supporto è accelerato dall'hardware HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>È necessario spazializzare?

La spazializzazione può migliorare molti suoni nelle applicazioni di realtà mista. La spazializzazione prende un suono dalla testa dell'ascoltatore e lo inserisce nel mondo. Per suggerimenti sull'uso efficace della spazializzazione nell'applicazione, vedere [Progettazione di suoni spaziali](spatial-sound-design.md).

### <a name="spatializer-personalization"></a>Personalizzazione dello spazializzatore

Gli HRTF modificano le differenze di livello e fase tra le orecchini nello spettro di frequenza. Si basano su modelli fisici e misurazioni della testa umana, del busto e delle forme dell'udito (pinnae). Il nostro cervello risponde a queste differenze per fornire una direzione percepita nel suono.

Ogni individuo ha una forma dell'uditivo, una dimensione della testa e una posizione dell'udito univoche. I migliori HRTF sono quindi conformi all'utente. Per aumentare l'accuratezza della spazializzazione, HoloLens usa la distanza inter-studentesca (IPD) dai display delle cuffia per regolare le HRTF per le dimensioni della testa.

### <a name="spatializer-platform-support"></a>Supporto della piattaforma di spazializzatori

Windows la spazializzazione, inclusi gli HRTF, tramite [l'API ISpatialAudioClient](/windows/win32/coreaudio/spatial-sound). Questa API espone alle applicazioni HoloLens 2'accelerazione hardware HRTF.

### <a name="spatializer-middleware-support"></a>Supporto del middleware spazializzatore

Il supporto per Windows HRTF è disponibile per i motori audio di terze parti seguenti.
* [Plug-in del motore audio Unity](../develop/unity/spatial-sound-in-unity.md)
* [Plug-in del motore audio Wwise](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>Acustica

L'audio spaziale non è altro che direzione. Altre dimensioni includono l'occlusione, l'ostruzione, il riverbero, il portale e la modellazione di origine. Collettivamente queste dimensioni sono definite *acustiche*. Senza acustica, i suoni spazializzati non hanno la distanza percepita.

I trattamento dell'acustica variano da semplice a complesso. È possibile usare un riverbero supportato da qualsiasi motore audio per eseguire il push dei suoni spazializzati nell'ambiente del listener. I sistemi acustici, ad esempio [Project Acustica,](/gaming/acoustics/what-is-acoustics) offrono un trattamento acustico più ricco e accattivante. Project L'acustica può modellare l'effetto di pareti, porte e altre geometrie della scena su un suono. È un'opzione efficace per i casi in cui la geometria della scena pertinente è nota in fase di sviluppo.

## <a name="next-steps"></a>Passaggi successivi

- [Audio spaziale in Unity](../develop/unity/spatial-sound-in-unity.md)
- [Come usare il suono nelle applicazioni di realtà mista](spatial-sound-design.md)