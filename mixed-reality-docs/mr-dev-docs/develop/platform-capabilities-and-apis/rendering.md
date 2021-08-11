---
title: Rendering
description: Informazioni su come il rendering olografico consente all'app di disegnare un ologramma in una posizione precisa nel mondo intorno all'utente.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: rendering, ologramma
ms.openlocfilehash: d01a5911ad8b479197bd38e8ed7825feef1f69dc51d2c2dc2f8e500e93880955
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193667"
---
# <a name="rendering"></a>Rendering

Il rendering olografico consente all'applicazione di disegnare un ologramma in una posizione precisa nel mondo intorno all'utente, indipendentemente dal fatto che sia posizionato esattamente nel mondo fisico o all'interno di un'area di autenticazione virtuale creata. [Ologrammi](../../discover/hologram.md) sono oggetti fatti di suono e luce. Il rendering consente all'applicazione di aggiungere la luce.

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

La chiave per il rendering olografico è conoscere il tipo di dispositivo in uso. I dispositivi **con see-through visualizzano**, [ad esempio HoloLens](/hololens/hololens1-hardware), aggiungono luce al mondo. I pixel neri sono completamente trasparenti, mentre i pixel più chiari sono sempre più opachi. Poiché la luce dei display viene aggiunta alla luce del mondo reale, i pixel bianchi sono traslucidi.

Anche se il rendering stereoscopico fornisce un segnale [](../../design/interaction-fundamentals.md) di profondità per gli ologrammi, l'aggiunta di effetti di messa a terra può aiutare gli utenti a vedere più facilmente la superficie vicina a un ologramma. Una tecnica di base consiste nell'aggiungere un alone intorno a un ologramma sulla superficie vicina e quindi eseguire il rendering di un'ombreggiatura su questo alone. In questo modo, l'ombreggiatura sembra sottrarre luce dall'ambiente. [L'audio](../../design/spatial-sound.md) spaziale è un altro segnale di profondità importante, consentendo agli utenti di capire la distanza e la posizione relativa di un ologramma.

I dispositivi **con schermi opachi,** [ad esempio Windows Mixed Reality visori VR immersive,](../../discover/immersive-headset-hardware-details.md)bloccano il mondo. I pixel neri sono di colore nero a tinta unita e qualsiasi altro colore viene visualizzato come tale per l'utente. L'applicazione è responsabile del rendering di tutti gli elementi visualizzati dall'utente. Questo rende ancora più importante mantenere una frequenza di aggiornamento costante in modo che gli utenti abbia un'esperienza comoda.

## <a name="predicted-rendering-parameters"></a>Parametri di rendering stimati

I visori VR di realtà mista (visori VR HoloLens e immersive) monitora continuamente la posizione e l'orientamento della testa dell'utente rispetto all'ambiente circostante. Quando l'applicazione inizia a preparare il frame successivo, il sistema stima dove sarà la testa dell'utente in futuro nel momento esatto in cui il fotogramma viene visualizzato sugli schermi. In base a questa stima, il sistema calcola la visualizzazione e le trasformazioni di proiezione da usare per tale frame. **L'applicazione deve usare queste trasformazioni per produrre risultati corretti.** Se le trasformazioni fornite dal sistema non vengono usate, l'immagine risultante non verrà allineata al mondo reale, causando la disagi dell'utente.

> [!NOTE]
> Per stimare con precisione quando un nuovo frame raggiungerà gli schermi, il sistema misura costantemente la latenza end-to-end effettiva della pipeline di rendering dell'applicazione. Anche se il sistema si adatta alla lunghezza della pipeline di rendering, è possibile migliorare la stabilità dell'ologramma mantenendo la pipeline il più breve possibile.

Le applicazioni che usano tecniche avanzate per aumentare la stima del sistema possono eseguire l'override delle trasformazioni di visualizzazione e proiezione di sistema. Queste applicazioni devono comunque usare trasformazioni fornite dal sistema come base per le trasformazioni personalizzate per produrre risultati significativi.

## <a name="other-rendering-parameters"></a>Altri parametri di rendering

Quando si esegue il rendering di un frame, il sistema specifica il viewport del buffer nascosto in cui deve essere disegnata l'applicazione. Questo riquadro di visualizzazione è spesso inferiore alle dimensioni complete del buffer dei frame. Indipendentemente dalle dimensioni del viewport, dopo il rendering del frame da parte dell'applicazione, il sistema ridimensiona l'immagine per riempire l'intero schermo.

Per le applicazioni che non riescono a eseguire il rendering con la frequenza di aggiornamento richiesta, è possibile configurare i parametri di [rendering](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) del sistema per ridurre l'utilizzo elevato di memoria e i costi di rendering a s costo di un aumento dell'aliasing dei pixel. È anche possibile modificare il formato del buffer nascosto, che per alcune app può contribuire a migliorare la larghezza di banda della memoria e la velocità effettiva in pixel.

Il frustum di rendering, la risoluzione e la frequenza dei fotogrammi in cui viene richiesto di eseguire il rendering dell'app possono anche cambiare da un frame all'altro e possono variare nell'occhio sinistro e destro. Ad esempio, [](/hololens/holographic-photos-and-videos) quando l'acquisizione di realtà mista (MRC) è attiva e la configurazione della visualizzazione [foto/videocamera](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) non è acconsentito esplicitamente, è possibile che venga eseguito il rendering di un occhio con una fov o una risoluzione più grande.

Per qualsiasi frame specificato, l'app *deve eseguire* il rendering usando la trasformazione di visualizzazione, la trasformazione di proiezione e la risoluzione del viewport fornite dal sistema. Inoltre, l'applicazione non deve mai presupporre che qualsiasi parametro di rendering o visualizzazione rimanga fisso da frame a frame. Motori come Unity gestiscono tutte queste trasformazioni nei propri oggetti fotocamera in modo che il movimento fisico degli utenti e lo stato del sistema sia sempre rispettato. Se l'applicazione consente lo spostamento virtuale dell'utente nel mondo (ad esempio, usando la levetta su un game pad), è possibile aggiungere un oggetto rig padre sopra la fotocamera che lo sposta. In questo modo la fotocamera riflette il movimento fisico e virtuale dell'utente. Se l'applicazione modifica la trasformazione di visualizzazione, la trasformazione di proiezione o la dimensione del viewport fornita dal sistema, deve informare il sistema chiamando [l'API di override appropriata.](/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)

Per migliorare la stabilità del rendering olografico, l'app deve fornire a Windows frame il buffer di profondità usato per il rendering. Se l'app fornisce un buffer di profondità, deve avere valori di profondità coerenti, con profondità espressa in metri dalla fotocamera. In questo modo il sistema può usare i dati di profondità per pixel per stabilizzare meglio il contenuto se la testa dell'utente finisce leggermente in offset rispetto alla posizione stimata. Se non si è in grado di fornire il buffer di profondità, è possibile specificare un punto di messa a fuoco e una normale, definendo un piano che taglia la maggior parte del contenuto. Se vengono forniti sia il buffer di profondità che un piano di messa a fuoco, il sistema potrebbe usarli entrambi. In particolare, è utile fornire sia il buffer di profondità che un punto di messa a fuoco che include un vettore di velocità quando l'applicazione visualizza ologrammi in movimento.

Per informazioni [dettagliate su questo argomento,](../native/rendering-in-directx.md) vedere l'articolo Rendering in DirectX.

## <a name="holographic-cameras"></a>Fotocamere olografiche

Windows Mixed Reality introduce il concetto di fotocamera **olografica.** Le fotocamere olografiche sono simili alla fotocamera tradizionale presente nei testi grafici 3D. Definiscono sia le proprietà estrisiche (posizione e orientamento) che le proprietà intrinseche della fotocamera. Ad esempio, il campo di visualizzazione viene usato per visualizzare una scena 3D virtuale. A differenza delle fotocamere 3D tradizionali, l'applicazione non ha il controllo della posizione, dell'orientamento e delle proprietà intrinseche della fotocamera. La posizione e l'orientamento della fotocamera olografica sono invece controllati implicitamente dal movimento dell'utente. Lo spostamento dell'utente viene inoltrato all'applicazione frame per frame tramite una trasformazione di visualizzazione. Analogamente, le proprietà intrinseche della fotocamera sono definite dall'ottico calibrato del dispositivo e inoltrate fotogramma per fotogramma tramite la trasformazione di proiezione.

In generale, l'applicazione eseguirà il rendering per una singola fotocamera stereo. Un ciclo di rendering affidabile supporterà più fotocamere e supporterà fotocamere mono e stereo. Ad esempio, il sistema potrebbe chiedere all'applicazione di eseguire il rendering da una prospettiva alternativa quando l'utente attiva una funzionalità come [Mixed Reality Capture](/hololens/holographic-photos-and-videos) (MRC), a seconda della forma del visore VR. Le applicazioni in grado di supportare più fotocamere le ottengono acconsentendo [esplicitamente](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) al [tipo](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) di fotocamere che possono supportare.

## <a name="volume-rendering"></a>Rendering dei volumi

Quando si esegue il rendering di mrI medici o volumi di progettazione in 3D, vengono spesso usate tecniche di [rendering](volume-rendering.md) dei volumi. Queste tecniche possono essere interessanti nella realtà mista, in cui gli utenti possono visualizzare naturalmente tale volume da angolazioni chiave, semplicemente spostando la testa.

## <a name="supported-resolutions-on-hololens-first-gen"></a>Risoluzioni supportate in HoloLens (prima generazione)

* La dimensione massima del viewport è una proprietà di [HolographicDisplay.](/uwp/api/windows.graphics.holographic.holographicdisplay) HoloLens è impostato sulla dimensione massima del viewport, ovvero 720p (1268x720), per impostazione predefinita.
* Le dimensioni del viewport possono essere modificate impostando ViewportScaleFactor in HolographicCamera. Questo fattore di scala è compreso nell'intervallo da 0 a 1.
* La dimensione minima supportata per il viewport HoloLens (prima generazione) è il 50% di 720p, ovvero 360p (634x360). Si tratta di un ViewportScaleFactor di 0,5.
* Qualsiasi valore inferiore a 540p non è consigliato a causa della riduzione delle prestazioni visive, ma può essere usato per identificare i colli di bottiglia in pixel fill rate.

## <a name="supported-resolutions-on-hololens-2"></a>Risoluzioni supportate in HoloLens 2

* Le dimensioni di destinazione di rendering correnti e massime supportate sono le proprietà della [configurazione della visualizzazione](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens 2 è impostato sulla dimensione massima della destinazione di rendering, ovvero 1440x936, per impostazione predefinita.
* Le app possono modificare le dimensioni dei buffer di destinazione di rendering chiamando il metodo RequestRenderTargetSize per richiedere una nuova dimensione di destinazione di rendering. Verranno scelte nuove dimensioni della destinazione di rendering, che soddisfano o superano le dimensioni della destinazione di rendering richieste. Questa API modifica le dimensioni del buffer di destinazione di rendering, che richiede la riallocazione della memoria nella GPU. Le implicazioni includono: le dimensioni della destinazione di rendering possono essere ridotte per ridurre l'utilizzo della memoria nella GPU e questo metodo non deve essere chiamato ad alta frequenza.
* Le app possono comunque modificare le dimensioni del viewport nello stesso modo in cui hanno fatto per HoloLens 1. Non è stata aggiunta alcuna riallocazione della memoria nella GPU, quindi può essere modificata con frequenza elevata, ma non può essere usata per ridurre l'utilizzo della memoria nella GPU.
* La dimensione minima supportata per il viewport HoloLens 2 è 634x412, viewportScaleFactor di circa 0,44 quando sono in uso le dimensioni predefinite della destinazione di rendering.
* Se vengono specificate dimensioni della destinazione di rendering inferiori alle dimensioni del viewport supportate più basse, il fattore di scala del viewport verrà ignorato.
* Qualsiasi valore inferiore a 540p non è consigliato a causa della riduzione delle prestazioni visive, ma può essere usato per identificare i colli di bottiglia in pixel fill rate.



## <a name="see-also"></a>Vedi anche
* [Stabilità degli ologrammi](hologram-stability.md)
* [Rendering in DirectX](../native/rendering-in-directx.md)