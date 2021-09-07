---
title: Rendering
description: Informazioni su come il rendering olografico consente all'app di disegnare un ologramma in una posizione precisa nel mondo intorno all'utente.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: rendering, ologramma
ms.openlocfilehash: 5bd06b9ca521e489a8944a1813b735a0fe1d60a5
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244223"
---
# <a name="holographic-rendering"></a>Rendering olografico

Il rendering olografico consente all'applicazione di disegnare un ologramma in una posizione precisa nel mondo intorno all'utente, indipendentemente dal fatto che sia posizionato con precisione nel mondo fisico o all'interno di un'area di autenticazione virtuale creata. [Ologrammi](../../discover/hologram.md) sono oggetti fatti di suono e luce. Il rendering consente all'applicazione di aggiungere la luce.

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
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Rendering</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Rendering olografico

La chiave per il rendering olografico è conoscere il tipo di dispositivo usato. I dispositivi **con display see-through,** [ad esempio HoloLens](/hololens/hololens1-hardware), aggiungono luce al mondo. I pixel neri sono completamente trasparenti, mentre i pixel più luminosi sono sempre più opachi. Poiché la luce dei display viene aggiunta alla luce dal mondo reale, i pixel bianchi sono traslucidi.

Anche se il rendering stereoscopico fornisce un'unica [](../../design/interaction-fundamentals.md) traccia di profondità per gli ologrammi, l'aggiunta di effetti di messa a terra può aiutare gli utenti a vedere più facilmente la superficie di un ologramma. Una tecnica di messa a terra consiste nell'aggiungere un bagliore intorno a un ologramma sulla superficie vicina e quindi eseguire il rendering di un'ombreggiatura su questo alone. In questo modo, l'ombreggiatura sembra sottrarre luce dall'ambiente. [Il suono spaziale](../../design/spatial-sound.md) è un altro importante segnale di profondità, consentendo agli utenti di capire la distanza e la posizione relativa di un ologramma.

I dispositivi **con schermi opachi,** [Windows Mixed Reality visori immersivi,](../../discover/immersive-headset-hardware-details.md)bloccano il mondo. I pixel neri sono di colore nero a tinta unita e qualsiasi altro colore viene visualizzato come colore per l'utente. L'applicazione è responsabile del rendering di tutto ciò che l'utente vede. Questo rende ancora più importante mantenere una frequenza di aggiornamento costante in modo che gli utenti hanno un'esperienza comoda.

## <a name="predicted-rendering-parameters"></a>Parametri di rendering stimati

I visori di realtà mista (HoloLens visori immersivi) monitora continuamente la posizione e l'orientamento della testa dell'utente rispetto all'ambiente circostante. Quando l'applicazione inizia a preparare il frame successivo, il sistema stima dove sarà la testa dell'utente in futuro nel momento esatto in cui il frame viene visualizzato sugli schermi. In base a questa stima, il sistema calcola la vista e la proiezione si trasforma da usare per tale frame. **L'applicazione deve usare queste trasformazioni per produrre risultati corretti.** Se le trasformazioni fornite dal sistema non vengono usate, l'immagine risultante non sarà allineata al mondo reale, causando disagi per l'utente.

> [!NOTE]
> Per stimare con precisione quando un nuovo frame raggiungerà gli schermi, il sistema misura costantemente la latenza end-to-end effettiva della pipeline di rendering dell'applicazione. Anche se il sistema si adatta alla lunghezza della pipeline di rendering, è possibile migliorare la stabilità dell'ologramma mantenendo la pipeline il più breve possibile.

Le applicazioni che usano tecniche avanzate per aumentare la stima del sistema possono eseguire l'override delle trasformazioni di visualizzazione di sistema e proiezione. Queste applicazioni devono comunque usare trasformazioni fornite dal sistema come base per le trasformazioni personalizzate per produrre risultati significativi.

## <a name="other-rendering-parameters"></a>Altri parametri di rendering

Quando si esegue il rendering di un frame, il sistema specifica il viewport del buffer nascosto in cui deve essere disegnata l'applicazione. Questo viewport è spesso più piccolo delle dimensioni complete del buffer dei frame. Indipendentemente dalle dimensioni del viewport, dopo il rendering del frame da parte dell'applicazione, il sistema ridimensiona l'immagine per riempire l'intero schermo.

Per le applicazioni che non riescono a eseguire il rendering alla frequenza di aggiornamento richiesta, è possibile configurare i parametri di [rendering](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) di sistema per ridurre la pressione della memoria e il costo di rendering a costo di un aumento dell'aliasing dei pixel. È anche possibile modificare il formato del buffer nascosto, che per alcune app può contribuire a migliorare la larghezza di banda della memoria e la velocità effettiva dei pixel.

Il frustum, la risoluzione e il framerate di rendering in cui viene richiesto di eseguire il rendering dell'app potrebbero anche cambiare da fotogramma a frame e potrebbero variare nell'occhio sinistro e destro. Ad esempio, [](/hololens/holographic-photos-and-videos) quando l'acquisizione di realtà mista (MRC) è attiva e la configurazione della visualizzazione di [foto/videocamere](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) non è esplicita, è possibile che venga eseguito il rendering di un occhio con una risoluzione o un FOV più grande.

Per qualsiasi frame specificato, l'app *deve eseguire* il rendering usando la trasformazione di visualizzazione, la trasformazione di proiezione e la risoluzione del viewport fornita dal sistema. Inoltre, l'applicazione non deve mai presupporre che qualsiasi parametro di rendering o visualizzazione rimanga fisso da frame a frame. Motori come Unity gestiscono tutte queste trasformazioni nei propri oggetti fotocamera in modo che lo spostamento fisico degli utenti e lo stato del sistema sia sempre rispettato. Se l'applicazione consente lo spostamento virtuale dell'utente attraverso il mondo (ad esempio usando la levetta su un gamepad), è possibile aggiungere un oggetto rig padre sopra la fotocamera che lo sposta. In questo modo la fotocamera riflette sia il movimento virtuale che il movimento fisico dell'utente. Se l'applicazione modifica la trasformazione della visualizzazione, la trasformazione di proiezione o la dimensione del viewport fornita dal sistema, deve informare il sistema chiamando [l'API di override appropriata.](/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)

Per migliorare la stabilità del rendering olografico, l'app deve fornire Windows ogni fotogramma il buffer di profondità usato per il rendering. Se l'app fornisce un buffer di profondità, deve avere valori di profondità coerenti, con profondità espressa in metri dalla fotocamera. In questo modo il sistema può usare i dati di profondità per pixel per stabilizzare meglio il contenuto se la testa dell'utente finisce leggermente in offset rispetto alla posizione stimata. Se non si è in grado di fornire il buffer di profondità, è possibile fornire un punto di messa a fuoco e una normale, definendo un piano che taglia la maggior parte del contenuto. Se vengono forniti sia il buffer di profondità che un piano di messa a fuoco, il sistema potrebbe usarli entrambi. In particolare, è utile fornire sia il buffer di profondità che un punto di messa a fuoco che include un vettore di velocità quando l'applicazione visualizza ologrammi in movimento.

Per informazioni [dettagliate su questo argomento,](../native/rendering-in-directx.md) vedere l'articolo Rendering in DirectX.

## <a name="holographic-cameras"></a>Fotocamere olografiche

Windows Mixed Reality introduce il concetto di fotocamera **olografica.** Le fotocamere olografiche sono simili alla fotocamera tradizionale presente nei testi grafici 3D; definiscono sia le proprietà esttriche (posizione e orientamento) che le proprietà intrinseche della fotocamera. Ad esempio, il campo di visualizzazione viene usato per visualizzare una scena 3D virtuale. A differenza delle fotocamere 3D tradizionali, l'applicazione non controlla la posizione, l'orientamento e le proprietà intrinseche della fotocamera. La posizione e l'orientamento della fotocamera olografica sono invece controllati in modo implicito dal movimento dell'utente. Lo spostamento dell'utente viene inoltrato all'applicazione frame per frame tramite una trasformazione di visualizzazione. Analogamente, le proprietà intrinseche della fotocamera sono definite dall'ottica calibrata del dispositivo e inoltrate fotogramma per fotogramma tramite la trasformazione di proiezione.

In generale, l'applicazione eseguirà il rendering per una singola fotocamera stereo. Un ciclo di rendering affidabile supporterà più fotocamere e supporterà fotocamere sia mono che stereo. Ad esempio, il sistema potrebbe chiedere all'applicazione di eseguire il rendering da una prospettiva alternativa quando l'utente attiva una funzionalità come [l'acquisizione](/hololens/holographic-photos-and-videos) di realtà mista (MRC), a seconda della forma del visore. Le applicazioni in grado di supportare più fotocamere le ottengono [optando per](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) il tipo [di](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) fotocamere che possono supportare.

## <a name="volume-rendering"></a>Rendering dei volumi

Quando si esegue il rendering di mrI medicali o volumi di progettazione in 3D, vengono spesso usate tecniche di [rendering](volume-rendering.md) dei volumi. Queste tecniche possono essere interessanti nella realtà mista, in cui gli utenti possono visualizzare naturalmente un volume di questo tipo da angolazioni chiave, semplicemente spostando la testa.

## <a name="supported-resolutions-on-hololens-first-gen"></a>Risoluzioni supportate in HoloLens (prima generazione)

* La dimensione massima del viewport è una proprietà di [HolographicDisplay.](/uwp/api/windows.graphics.holographic.holographicdisplay) HoloLens è impostato sulla dimensione massima del viewport, ovvero 720p (1268x720), per impostazione predefinita.
* Le dimensioni del viewport possono essere modificate impostando ViewportScaleFactor in HolographicCamera. Questo fattore di scala è compreso nell'intervallo da 0 a 1.
* La dimensione minima supportata del viewport HoloLens (prima generazione) è il 50% di 720p, ovvero 360p (634x360). Si tratta di un ViewportScaleFactor di 0,5.
* Qualsiasi valore inferiore a 540p non è consigliato a causa della riduzione dell'oggetto visivo, ma può essere usato per identificare i colli di bottiglia nei pixel fill rate.

## <a name="supported-resolutions-on-hololens-2"></a>Risoluzioni supportate in HoloLens 2

* Le dimensioni correnti e massime della destinazione di rendering supportate sono proprietà della [configurazione della visualizzazione](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens 2 è impostato sulla dimensione massima della destinazione di rendering, ovvero 1440x936, per impostazione predefinita.
* Le app possono modificare le dimensioni dei buffer di destinazione di rendering chiamando il metodo RequestRenderTargetSize per richiedere una nuova dimensione di destinazione di rendering. Verrà scelta una nuova dimensione della destinazione di rendering, che soddisfa o supera le dimensioni della destinazione di rendering richiesta. Questa API modifica le dimensioni del buffer di destinazione di rendering, che richiede la riallocazione della memoria nella GPU. Le implicazioni di questo tipo includono: le dimensioni della destinazione di rendering possono essere ridotte per ridurre l'utilizzo della memoria nella GPU e questo metodo non deve essere chiamato con frequenza elevata.
* Le app possono comunque modificare le dimensioni del viewport nello stesso modo in cui sono HoloLens 1. Non è stata aggiunta alcuna rilocazione della memoria nella GPU, quindi può essere modificata con frequenza elevata, ma non può essere usata per ridurre l'utilizzo della memoria nella GPU.
* La dimensione minima supportata del viewport HoloLens 2 è 634x412, viewportScaleFactor di circa 0,44 quando sono in uso le dimensioni predefinite della destinazione di rendering.
* Se vengono specificate dimensioni della destinazione di rendering inferiori alle dimensioni del viewport supportate più basse, il fattore di scala del viewport verrà ignorato.
* Qualsiasi valore inferiore a 540p non è consigliato a causa della riduzione dell'oggetto visivo, ma può essere usato per identificare i colli di bottiglia nei pixel fill rate.



## <a name="see-also"></a>Vedi anche
* [Stabilità degli ologrammi](hologram-stability.md)
* [Rendering in DirectX](../native/rendering-in-directx.md)