---
title: Criteri di qualità delle app
description: Questo documento descrive i fattori principali che influiscono sulla qualità delle app di realtà mista.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criteri di qualità delle app, realtà mista, app di realtà mista, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale
ms.openlocfilehash: 858b0782c4e6754ee6753d463d5fe498e3a893f6c21b3f1c86ac14f8c0e6c8cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189382"
---
# <a name="app-quality-criteria"></a>Criteri di qualità delle app

Questo documento descrive i fattori principali che influiscono sulla qualità delle app di realtà mista. Per ogni fattore, vengono fornite le informazioni seguenti
* Panoramica: una breve descrizione del fattore di qualità e del motivo per cui è importante.
* Impatto del dispositivo: il tipo di dispositivo Windows Mixed Reality interessato.
* Criteri di qualità: come valutare il fattore di qualità.
* Come misurare: metodi per misurare (o sperimentare) il problema.
* Consigli: riepilogo degli approcci per offrire un'esperienza utente migliore.
* Risorse: risorse pertinenti per sviluppatori e progettazione utili per creare esperienze di app migliori.

## <a name="frame-rate"></a>Frequenza dei fotogrammi

La frequenza dei fotogrammi è il primo pilastro della stabilità degli ologrammi e del comfort dell'utente. La frequenza dei fotogrammi al di sotto delle destinazioni consigliate può causare l'instabilità degli ologrammi, con un impatto negativo sull'affidabilità dell'esperienza e potenzialmente causando l'affaticamento oculare. La frequenza dei fotogrammi di destinazione per l'esperienza nei visori VR immersive di Windows Mixed Reality è di 60 Hz o 90 Hz a seconda dei PC compatibili con Windows Mixed Reality supportati. Ad HoloLens, la frequenza dei fotogrammi di destinazione è 60 Hz.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
| L'app soddisfa in modo coerente l'obiettivo dei fotogrammi al secondo (FPS) per il dispositivo di destinazione: 60 fps HoloLens; 90 fps su PC Ultra; e 60 fps nei PC Mainstream. | L'app presenta interruzioni intermittenti dei frame che non ostacolano l'esperienza di base o FPS è costantemente inferiore all'obiettivo desiderato, ma non impedisce l'esperienza dell'app. | L'app sta riscontrando un calo della frequenza dei fotogrammi in media ogni 10 secondi o meno. |

### <a name="how-to-measure"></a>Come misurare

* Un grafico della frequenza dei fotogrammi in tempo reale viene fornito dal Windows Portale di dispositivi [in](using-the-windows-device-portal.md#system-performance) "Prestazioni del sistema".
* Per il debug dello sviluppo, aggiungere un contatore di diagnostica della frequenza dei fotogrammi nell'app. Vedere Risorse per un contatore di esempio.
* I calo della frequenza dei fotogrammi possono essere riscontrati nel dispositivo mentre l'app è in esecuzione spostando la testa da un lato all'altro. Se l'ologramma mostra movimenti instabilità imprevisti, la causa è probabilmente una bassa frequenza dei fotogrammi o il piano di stabilità.

### <a name="recommendations"></a>Consigli

* Aggiungere un contatore della frequenza dei fotogrammi all'inizio del lavoro di sviluppo.
* Le modifiche che comportano un calo della frequenza dei fotogrammi devono essere valutate e risolte in modo appropriato come bug delle prestazioni.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Stabilità e frequenza fotogrammi dell'ologramma](hologram-stability.md#frame-rate)
* [Budget delle prestazioni degli asset](../../design/asset-creation-process.md)
* [Consigli sulle prestazioni per Unity](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Realtà mista Toolkit, visualizzazione del contatore FPS](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [Realtà mista Toolkit, shader](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Riferimenti esterni

* [Unity, Ottimizzazione delle applicazioni per dispositivi mobili](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Stabilità degli ologrammi

Gli ologrammi stabili aumentano l'usabilità e l'affidabilità dell'app e creano un'esperienza di visualizzazione più comoda per l'utente. La qualità della stabilità dell'ologramma è il risultato di un buon sviluppo di app e della capacità del dispositivo di comprendere (tenere traccia) dell'ambiente. Sebbene la frequenza dei fotogrammi sia il primo elemento fondamentale della stabilità, altri fattori possono influire sulla stabilità, tra cui:

* Uso del piano di stabilizzazione
* Distanza da ancoraggi nello spaziale
* Rilevamento

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  Ologrammi appaiono costantemente stabili. | Il contenuto secondario mostra uno spostamento imprevisto. o lo spostamento imprevisto non ostacola l'esperienza complessiva dell'app. | Il contenuto primario nel frame mostra uno spostamento imprevisto. |

### <a name="how-to-measure"></a>Come misurare

Durante il controllo del dispositivo e la visualizzazione dell'esperienza:

* Spostare la testa da un lato all'altro. Se gli ologrammi mostrano un movimento imprevisto, la causa probabile è una bassa frequenza dei fotogrammi o un allineamento non corretto del piano di stabilità al piano focale.
* Spostarsi all'esterno degli ologrammi e dell'ambiente, cercare comportamenti come la corsia e il jumpiness. Questo tipo di movimento è probabilmente causato dal dispositivo che non traccia l'ambiente o dalla distanza dall'ancoraggio nello spaziale.
* Se nel fotogramma sono presenti ologrammi di grandi dimensioni o più, osservare il comportamento dell'ologramma a varie profondità mentre si sposta la posizione della testa da un lato all'altro, se si verifica un'ombreggiatura probabilmente causata dal piano di stabilizzazione.

### <a name="recommendations"></a>Consigli

* Aggiungere un contatore della frequenza dei fotogrammi all'inizio del lavoro di sviluppo.
* Usare il piano di stabilizzazione.
* Eseguire sempre il rendering degli ologrammi ancorati entro 3 metri dal relativo ancoraggio.
* Assicurarsi che l'ambiente sia configurato per il rilevamento corretto.
* Progettare l'esperienza per evitare ologrammi a vari livelli di profondità focale all'interno del fotogramma.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Stabilità e frequenza fotogrammi dell'ologramma](hologram-stability.md#frame-rate)
* [Case study, Uso del piano di stabilizzazione](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Consigli sulle prestazioni per Unity](../unity/performance-recommendations-for-unity.md)
* [Ancoraggi nello spazio](../../design/spatial-anchors.md)
* [Gestione degli errori di rilevamento](../../design/coordinate-systems.md#handling-tracking-errors)
* [Frame di riferimento zionario](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [MR Companion Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Ologrammi posizione su superfici reali

I disallineamenti degli ologrammi con oggetti fisici (se destinati a essere posizionati l'uno rispetto all'altro) sono un'indicazione chiara della non unione di ologrammi e del mondo reale. L'accuratezza del posizionamento deve essere relativa alle esigenze dello scenario. Ad esempio, il posizionamento generale della superficie può usare la mappa spaziale, ma un posizionamento più accurato richiederà un uso di marcatori e calibrazione.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
| Ologrammi allinearsi alla superficie in genere nell'intervallo centimetri-pollici. Se è necessaria una maggiore accuratezza, l'app deve fornire un mezzo efficiente per la collaborazione all'interno della specifica dell'app. | N/D | Gli ologrammi appaiono non allineati all'oggetto di destinazione fisico interrompendo il piano di superficie o apparendo come fluttuanti dalla superficie. Se è necessaria l'accuratezza, Ologrammi deve soddisfare la specifica di prossimità dello scenario. | 

### <a name="how-to-measure"></a>Come misurare

* Ologrammi posizionati sulla mappa spaziale non dovrebbero apparire notevolmente fluttuanti sopra o sotto la superficie.
* Ologrammi che richiedono un posizionamento accurato devono avere una qualche forma di marcatore e sistema di calibrazione che sia accurato in base alle esigenze dello scenario.

### <a name="recommendations"></a>Consigli

* La mappa spaziale è utile per posizionare oggetti su superfici quando la precisione non è necessaria.
* Per una precisione ottimale, usare marcatori o poster per impostare gli ologrammi e un controller Xbox (o un meccanismo di allineamento manuale) per la calibrazione finale.
* Valutare la possibilità di suddividere gli ologrammi di grandi dimensioni in parti logiche e di allineare ogni parte alla superficie.
* Anche l'impostazione non corretta della distanza interpupillaria (IPD) può avere effetto sull'allineamento dell'ologramma. Configurare sempre HoloLens per l'IPD dell'utente.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Posizionamento del mapping spaziale](../../design/spatial-mapping.md#placement)
* [Processo di analisi della stanza](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Procedure consigliate per gli ancoraggi nello spaziale](../../design/spatial-anchors.md#best-practices)
* [Gestione degli errori di rilevamento](../../design/coordinate-systems.md#handling-tracking-errors)
* [Mapping spaziale in Unity](../unity/spatial-mapping-in-unity.md)
* [Panoramica dello sviluppo di Vuforia](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [MR Toolkit, librerie di mapping spaziale](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [Kit complementare MR, esempio di calibrazione poster](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [Mr Companion Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Riferimenti esterni

* [Case study lowes, allineamento di precisione](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Visualizzazione della zona di comfort

Gli sviluppatori di app controllano dove convergono gli occhi degli utenti posizionando contenuto e ologrammi a varie profondità. Gli utenti HoloLens possono sempre mantenere un'immagine chiara a 2,0 m perché i display HoloLens sono fissi a una distanza ottica di circa 2,0 m dall'utente. Una profondità del contenuto non corretta può causare disagio visivo o affaticamento.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

<table>
<tr>
<td> Ottimale </td><td><ul>
<li>Posizionare il contenuto a 2 m.</li><li>Quando gli ologrammi non possono essere posizionati a 2 m e non è possibile evitare conflitti tra convergenza e sistemazione, la zona ottimale per il posizionamento degli ologrammi è compresa tra 1,25 e 5 m.</li><li>In ogni caso, i progettisti devono strutturare il contenuto per invitare gli utenti a interagire a più di 1 m di distanza (ad esempio, regolare le dimensioni del contenuto e i parametri di posizionamento predefiniti).</li><li>A meno che non sia richiesto dallo scenario, un piano di ritaglio deve essere implementato con dissolvenza in uscita a partire da 1 m.</li><li>Nei casi in cui è necessaria un'osservazione più vicina di un ologramma senza movimento, il contenuto non deve essere più vicino a 50 cm.</li>
</ul></td>
</tr><tr>
<td> Incontra</td><td> Il contenuto si trova all'interno delle linee guida di visualizzazione e movimento, ma non viene utilizzato in modo improprio o non viene utilizzato il piano di ritaglio.</td>
</tr><tr>
<td> Esito negativo </td><td> Il contenuto viene presentato troppo vicino (in genere &lt; 1,25 m o 50 cm per gli ologrammi stazionari che &lt; richiedono un'osservazione più vicina).</td>
</tr>
</table>

### <a name="how-to-measure"></a>Come misurare

* Il contenuto deve in genere essere a 2 metri di distanza, ma non più vicino a 1,25 o oltre 5 m.
* Con poche eccezioni, la distanza HoloLens di rendering di ritaglio deve essere impostata su 85CM con dissolvenza in uscita dal contenuto a partire da 1 m. Avvicinarsi al contenuto e notare l'effetto del piano di ritaglio.
* Il contenuto stazionario non deve essere più vicino a 50 cm di distanza.

### <a name="recommendations"></a>Consigli

* Progettare il contenuto per una distanza di visualizzazione ottimale di 2 m.
* Impostare la distanza di rendering del ritaglio su 85 cm con dissolvenza del contenuto a partire da 1 m.
* Per gli ologrammi stazionari che necessitano di una visualizzazione più vicina, il piano di ritaglio non deve essere più vicino a 30 cm e la dissolvenza in uscita deve iniziare ad almeno 10 cm dal piano di ritaglio.

### <a name="resources"></a>Risorse

* [Distanza di rendering](hologram-stability.md#hologram-render-distances)
* [Punto focale in Unity](../unity/focus-point-in-unity.md)
* [Sperimentazione della scalabilità](../../design/scale.md#experimenting-with-scale)
* [Testo, Dimensioni del carattere consigliate](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a>Cambio di profondità

Indipendentemente dalla zona di visualizzazione dei problemi di comfort, le richieste per l'utente di passare spesso o rapidamente tra oggetti focali vicini e lontani (inclusi gli ologrammi e il contenuto reale) possono causare affaticamento oculomotore e disagio generale.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  Cambio di profondità limitato o naturale che non causa il riorientamento innaturale dell'utente. | Un cambio di profondità improvviso è fondamentale e progettato per l'esperienza dell'app o per un cambio di profondità improvviso causato da contenuto reale imprevisto. | Cambio di profondità coerente o cambio di profondità improvviso che non è necessario o core per l'esperienza dell'app. | 

### <a name="how-to-measure"></a>Come misurare

* Se l'app richiede all'utente di modificare in modo coerente e/o improvviso lo stato attivo della profondità, si verifica un problema di cambio di profondità.

### <a name="recommendations"></a>Consigli

* Mantenere il contenuto primario su un piano focale coerente e assicurarsi che il piano di stabilizzazione corrisponda al piano focale. Ciò allevierà l'affaticamento oculomotore e il movimento imprevisto dell'ologramma.

### <a name="resources"></a>Risorse

* [Distanza di rendering](hologram-stability.md#hologram-render-distances)
* [Punto focale in Unity](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Uso del suono spaziale

In Windows Mixed Reality, il motore audio fornisce il componente aurale dell'esperienza di realtà mista simulando il suono 3D usando la direzione, la distanza e le simulazioni ambientali. L'uso del suono spaziale in un'applicazione consente agli sviluppatori di posizionare in modo convincente i suoni in uno spazio tridimensionale (sfera) intorno all'utente. Questi suoni sembrano quindi pro venire da oggetti fisici reali o da ologrammi di realtà mista nell'ambiente dell'utente. Il suono spaziale è uno strumento potente per l'esperienza utente, l'accessibilità e la progettazione in applicazioni di realtà mista.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  Il suono è spazializzato logicamente e l'esperienza utente usa in modo appropriato il suono per facilitare l'individuazione degli oggetti e il feedback dell'utente. Il suono è naturale e rilevante per gli oggetti e normalizzato in tutto lo scenario. | L'audio spaziale viene usato in modo appropriato per migliorare l'affidabilità, ma manca come mezzo per facilitare il feedback e l'individuabilità degli utenti. | L'audio non è spazializzato come previsto e/o la mancanza di audio per assistere l'utente all'interno dell'esperienza utente. Oppure l'audio spaziale non è stato considerato o usato nella progettazione dello scenario. | 

### <a name="how-to-measure"></a>Come misurare

* In generale, i suoni pertinenti devono emettere dagli ologrammi di destinazione (ad esempio, il suono del suono del suono proveniente da un cane olografico).
* I segnali acustici devono essere usati in tutta l'esperienza utente per aiutare l'utente a inviare commenti o suggerimenti sulle azioni all'esterno della cornice olografica.

### <a name="recommendations"></a>Consigli

* Usare l'audio spaziale per facilitare l'individuazione di oggetti e le interfacce utente.
* I suoni reali funzionano meglio della sintesi o dell'audio non naturale.
* La maggior parte dei suoni deve essere spazializzata.
* Evitare emettitori invisibili.
* Evitare la maschera spaziale.
* Normalizzare tutti i suoni.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Audio spaziale](../../design/spatial-sound.md)
* [Progettazione dell'audio spaziale](../../design/spatial-sound-design.md)
* [Audio spaziale in Unity](../unity/spatial-sound-in-unity.md)
* [Case study, Audio spaziale per HoloTour](../../design/case-study-spatial-sound-design-for-holotour.md)
* [Case study, Using spatial sound in RoboRaid](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Realtà mista Toolkit - Audio spaziale](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Concentrarsi sui limiti della cornice olografica (FOV)

Esperienze utente ben progettate possono creare e mantenere un contesto utile dell'ambiente virtuale che si estende agli utenti. La mitigazione dell'effetto dei limiti fov comporta una progettazione precisa della scalabilità e del contesto del contenuto, dell'uso di audio spaziale, dei sistemi di indicazioni e della posizione dell'utente. Se l'operazione è stata eseguita nel modo giusto, l'utente sarà meno compromesso dai limiti di fov, pur avendo un'esperienza di app comoda.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  L'utente non perde mai il contesto e la visualizzazione è comoda. Viene fornita assistenza sul contesto per oggetti di grandi dimensioni. Vengono fornite indicazioni per l'individuabilità e la visualizzazione per gli oggetti esterni al frame. In generale, la progettazione del movimento e la scala degli ologrammi sono appropriate per un'esperienza di visualizzazione comoda. | L'utente non perde mai il contesto, ma potrebbe essere necessario un movimento aggiuntivo in situazioni limitate. In situazioni limitate la scala fa sì che gli ologrammi interrompano il fotogramma verticale o orizzontale causando la visualizzazione degli ologrammi da parte di alcuni movimenti di movimento. | Per visualizzare gli ologrammi, è probabile che l'utente perda il contesto e/o il movimento del collo coerente. Non sono disponibili indicazioni di contesto per oggetti olografici di grandi dimensioni, lo spostamento di oggetti facili da perdere all'esterno del frame senza indicazioni di individuabilità o ologrammi alti richiede un movimento regolare del movimento del movimento di movimento. | 

### <a name="how-to-measure"></a>Come misurare

* Il contesto per un ologramma (di grandi dimensioni) viene perso o non viene compreso a causa del ritagliato ai limiti.
* Le posizioni degli ologrammi sono difficili da trovare a causa della mancanza di attenzione o del contenuto che si sposta rapidamente all'interno e all'esterno della cornice olografica.
* Lo scenario richiede un movimento della testa regolare e ripetitivo verso l'alto e verso il basso per visualizzare completamente un ologramma con conseguente affaticamento del collo.

### <a name="recommendations"></a>Consigli

* Iniziare l'esperienza con oggetti di piccole dimensioni che si adattano alla fov, quindi eseguire la transizione con segnali visivi a versioni più grandi.
* Usare audio spaziale e attenzione per aiutare l'utente a trovare contenuto esterno alla fov.
* Per quanto possibile, evitare gli ologrammi che ritagliano verticalmente la fov.
* Fornire all'utente indicazioni in-app per una migliore posizione di visualizzazione.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Frame olografico](../../design/holographic-frame.md)
* [Case study, apprendimento HoloStudio'interfaccia utente e progettazione delle interazioni](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Scalabilità di oggetti e ambienti](../../design/scale.md)
* [Cursori, segnali visivi](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a>Riferimenti esterni

* [Grande distorsio sull'fov](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>Il contenuto reagisce alla posizione dell'utente

Ologrammi deve reagire alla posizione dell'utente approssimativamente come gli oggetti "reali". Una considerazione di progettazione importante è data da elementi dell'interfaccia utente che non possono necessariamente presupporre che la posizione di un utente sia stazionaria e adattata al movimento dell'utente. La progettazione di un'app che si adatta correttamente alla posizione dell'utente creerà un'esperienza più facilmente utilizzabile.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

<table>
<tr>
<td> Ottimale </td><td> Il contenuto e l'interfaccia utente si adattano alle posizioni dell'utente consentendo all'utente di interagire naturalmente con il contenuto nell'ambito dello spostamento previsto dell'utente.</td>
</tr><tr>
<td> Incontra </td><td> L'interfaccia utente si adatta alla posizione dell'utente, ma può ostacolare la visualizzazione del contenuto chiave che richiede all'utente di modificare la propria posizione.</td>
</tr><tr>
<td> Esito negativo </td><td><ol>
<li>Gli elementi dell'interfaccia utente vengono persi o bloccati durante lo spostamento causando il ritorno innaturale dell'utente ai controlli (o trova).</li><li>Gli elementi dell'interfaccia utente limitano la visualizzazione del contenuto primario.</li><li>Lo spostamento dell'interfaccia utente non è ottimizzato per la visualizzazione della distanza e della distanza, in particolare con <a href="../../design/billboarding-and-tag-along.md">gli elementi dell'interfaccia utente con tag.</a></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Come misurare

* Tutte le misurazioni devono essere eseguite in un ambito ragionevole dello scenario. Anche se lo spostamento dell'utente può variare, non tentare di schernire l'app con movimenti estremi dell'utente.
* Per gli elementi dell'interfaccia utente, i controlli pertinenti devono essere disponibili indipendentemente dal movimento dell'utente. Ad esempio, se l'utente sta visualizzando e aggirando una mappa 3D con zoom, il controllo zoom deve essere immediatamente disponibile per l'utente indipendentemente dalla posizione.

### <a name="recommendations"></a>Consigli

* L'utente è la fotocamera e controlla il movimento. Lasciarli guidare.
* Prendere in considerazione la possibilità di creare testo e sistemi di menu che altrimenti verrebbero bloccati o nascosti se un utente si spostasse.
* Usare tag-along per il contenuto che deve seguire l'utente, consentendo comunque all'utente di vedere cosa si trova davanti a loro.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Progettazione delle interazioni](../../discover/hologram.md)
* [Colore, luce e materiale](../../design/color-light-and-materials.md)
* [Billboarding e tag-along](../../design/billboarding-and-tag-along.md)
* [Interazioni istintive](../../design/interaction-fundamentals.md)
* [Movimento autonomo e locomozione dell'utente](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a>Chiarezza dell'interazione con l'input

La chiarezza dell'interazione con l'input è fondamentale per l'usabilità di un'app e include coerenza dell'input, approccio, individuabilità dei metodi di interazione. L'utente può usare interazioni comuni a livello di piattaforma senza rilearning. Se l'app ha un input personalizzato, deve essere chiaramente comunicata e illustrata.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  I metodi di interazione di input sono coerenti con Windows Mixed Reality indicazioni [fornite.](../../design/interaction-fundamentals.md) Qualsiasi input personalizzato non deve essere ridondante con l'input standard (piuttosto usare l'interazione standard) e deve essere chiaramente comunicato e dimostrato all'utente. | Analogamente alla migliore, ma gli input personalizzati sono ridondanti con metodi di input standard. L'utente può comunque raggiungere l'obiettivo e lo stato di avanzamento tramite l'esperienza dell'app. | Mapping del metodo o del pulsante di input difficile da comprendere. L'input è fortemente personalizzato, non supporta l'input standard, non contiene istruzioni o può causare problemi di affaticamento e comfort. | 

### <a name="how-to-measure"></a>Come misurare

* L'app usa metodi [di input standard coerenti.](../../design/interaction-fundamentals.md)
* Se l'app ha input personalizzato, viene comunicata chiaramente tramite:
* Esperienza di prima esecuzione
* Schermate introduttive
* Descrizioni comando
* Coach mano
* Sezione della Guida
* Voce over

### <a name="recommendations"></a>Consigli

* Usare metodi di input standard quando possibile.
* Fornire dimostrazioni, esercitazioni e descrizioni comando per metodi di input non standard.
* Usare un modello di interazione coerente in tutta l'app.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Interazioni istintive](../../design/interaction-fundamentals.md)
* [Oggetti interagiscibili](../../design/interactable-object.md)
* [Puntamento con la testa e attesa](../../design/gaze-and-dwell.md)
* [Cursori](../../design/cursors.md)
* [Comfort e sguardo](../../design/comfort.md#gaze-direction)
* [Input vocale](../../design/voice-input.md)
* [Controller del movimento](../../design/motion-controllers.md)
* [Guida alla conversione dell'input per Unity](../porting-apps/input-porting-guide-for-unity.md)
* [Input da tastiera in Unity](../unity/keyboard-input-in-unity.md)
* [Sguardo fisso in Unity](../unity/gaze-in-unity.md)
* [Controller di movimento in Unity](../unity/motion-controllers-in-unity.md)
* [Movimenti in Unity](../unity/gestures-in-unity.md)
* [Input vocale in Unity](../unity/voice-input-in-unity.md)
* [Input da tastiera, mouse e controller in DirectX](./keyboard-mouse-and-controller-input-in-directx.md)
* [Puntamento con la testa e sguardo fisso in DirectX](../native/gaze-in-directx.md)
* [Mani e controller del movimento in DirectX](../native/hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Case study: Ricerca di un maggiore personal computing](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Studio del cast: HoloStudio di progettazione dell'interfaccia utente e dell'interazione](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [App di esempio: tabella periodica degli elementi](../unity/periodic-table-of-the-elements.md)
* [App di esempio: modulo Lunare](../unity/lunar-module.md)

## <a name="interactable-objects"></a>Oggetti interagiscibili

Un pulsante è stato a lungo una metafora usata per attivare un evento nel mondo astratto 2D. Nel mondo della realtà mista tridimensionale non è più necessario limitarsi a questo mondo di astrazione. Qualsiasi oggetto può essere un oggetto interactable che attiva un evento. Un oggetto interagiscibile può essere rappresentato come qualsiasi cosa, da una tazzina di caffè sul tavolo a un palloncino mobile nell'aria. Indipendentemente dal modulo, gli oggetti interagibili devono essere chiaramente riconoscibili dall'utente tramite segnali visivi e audio.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  Indipendentemente dal modulo, gli oggetti interagiscibili sono riconoscibili tramite segnali visivi e audio in tre stati: inattivo, di destinazione e selezionato. "See it, say it" è chiaro e coerentemente usato in tutta l'esperienza. Gli oggetti vengono ridimensionati e distribuiti per consentire la destinazione senza errori. | L'utente può riconoscere l'oggetto come interagiscibile tramite feedback audio o visivo e può scegliere come destinazione e attivare l'oggetto. | In assenza di segnali visivi o audio, l'utente non può riconoscere un oggetto interagiscibile. Le interazioni sono erre erre a causa della scala degli oggetti o della distanza tra gli oggetti. | 

### <a name="how-to-measure"></a>Come misurare

* Gli oggetti interagibili sono riconoscibili come "interagiscibili"; inclusi pulsanti, menu e contenuto specifico dell'app. Come regola generale, devono essere presenti un segnale visivo e audio per gli oggetti interagiscibili come destinazione.

### <a name="recommendations"></a>Consigli

* Usare feedback visivo e audio per le interazioni.
* Il feedback visivo deve essere differenziato per ogni stato di input (inattivo, di destinazione, selezionato)
* Gli oggetti interagibili devono essere ridimensionati e posizionati per la destinazione senza errori.
* Gli oggetti interagibili raggruppati, ad esempio una barra dei menu o un elenco, devono avere una spaziatura appropriata per la destinazione.
* I pulsanti e i menu che supportano i comandi vocali devono fornire etichette di testo per la parola chiave del comando ("See it, say it")

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Oggetto che supporta interazioni](../../design/interactable-object.md)
* [Testo in Unity](../unity/text-in-unity.md)
* [Rettangolo di selezione e barra dell'app](../../design/app-bar-and-bounding-box.md)
* [Input vocale](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Realtà mista Toolkit - Esperienza utente](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Analisi della stanza

Le app che richiedono dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente questi dati nel tempo e tra sessioni mentre l'utente esplora l'ambiente con il dispositivo attivo. La completezza e la qualità di questi dati dipendono da una serie di fattori, tra cui la quantità di esplorazione eseguita dall'utente, il tempo passato dall'esplorazione e se oggetti come mobili e porte sono stati spostati dopo che il dispositivo ha analizzato l'area. Molte app analizzeranno i dati di mapping spaziale all'inizio dell'esperienza per valutare se l'utente deve eseguire passaggi aggiuntivi per migliorare la completezza e la qualità della mappa spaziale. Se l'utente deve analizzare l'ambiente, è necessario fornire indicazioni chiare durante l'esperienza di analisi.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  La visualizzazione della mesh spaziale consente di indicare agli utenti che è in corso l'analisi. L'utente sa chiaramente cosa fare e quando l'analisi viene avviata e arrestata. | Viene fornita la visualizzazione della mesh spaziale, ma l'utente potrebbe non sapere chiaramente cosa fare e non vengono fornite informazioni sullo stato di avanzamento. | Nessuna visualizzazione della mesh. Nessuna indicazione fornita all'utente riguardo a dove cercare o quando viene avviata/arrestata l'analisi. |

### <a name="how-to-measure"></a>Come misurare

* Durante l'analisi di una stanza richiesta, vengono fornite indicazioni visive e audio che indicano dove guardare e quando avviare e arrestare l'analisi.

### <a name="recommendations"></a>Consigli

* Indicare la quantità del volume totale nelle vicinanze degli utenti che deve far parte dell'esperienza.
* Comunicare all'avvio e all'arresto dell'analisi, ad esempio un indicatore di stato.
* Usare una visualizzazione della mesh durante l'analisi.
* Fornire segnali visivi e audio per incoraggiare l'utente a guardare e spostarsi nella stanza.
* Informare l'utente dove andare per migliorare i dati. In molti casi, può essere meglio indicare all'utente cosa deve fare (ad esempio, guardare il limite massimo, guardare dietro le quinte), per ottenere la qualità di analisi necessaria.

### <a name="resources"></a>Risorse

#### <a name="documentation"></a>Documentazione

* [Visualizzazione della scansione dello spazio](../../design/room-scan-visualization.md)
* [Case study: Espansione delle funzionalità di mapping spaziale di HoloLens](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Case study: Progettazione dell'audio spaziale per HoloTour](../../design/case-study-spatial-sound-design-for-holotour.md)
* [Case study: Creazione di un'esperienza immersiva in frammenti](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Strumenti ed esercitazioni

* [Realtà mista Toolkit - Esperienza utente](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicatori direzionali

In un'app di realtà mista, il contenuto potrebbe non rientrare nel campo di visualizzazione o essere occluso da oggetti reali. Un'app ben progettata semplifica la ricerca di contenuto non visibile per l'utente. Gli indicatori direzionali avvisano un utente di contenuti importanti e forniscono indicazioni sul contenuto in relazione alla posizione dell'utente. Le linee guida per il contenuto non visibile possono assumere la forma di emettitori audio, frecce direzionali o segnali visivi diretti.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  I segnali visivi e audio guidano direttamente l'utente verso il contenuto pertinente all'esterno del campo visivo. | Freccia o indicatore che punta l'utente nella direzione generale del contenuto. | Il contenuto pertinente non rientra nel campo di visualizzazione e all'utente non viene fornita alcuna indicazione sulla posizione. | 

### <a name="how-to-measure"></a>Come misurare

* Il contenuto pertinente all'esterno del campo di visualizzazione dell'utente è individuabile tramite segnali visivi e/o audio.

### <a name="recommendations"></a>Consigli

* Quando il contenuto pertinente non rientra nel campo di visualizzazione dell'utente, usare indicatori direzionali e segnali audio per guidare l'utente verso il contenuto. In molti casi è preferibile una guida visiva diretta rispetto alle frecce direzionali.
* Gli indicatori direzionali non devono essere incorporati nel cursore.

### <a name="resources"></a>Risorse

* [Frame olografico](../../design/holographic-frame.md)

## <a name="data-loading"></a>Caricamento dei dati

Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata. Può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare il tempo di attesa.

### <a name="device-impact"></a>Impatto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criteri di qualità

|  Ottimale  |  Incontra |  Esito negativo |
--- | --- | ---
|  Indicatore visivo animato, sotto forma di indicatore di stato o anello, che mostra lo stato di avanzamento durante il caricamento o l'elaborazione dei dati. L'indicatore visivo fornisce indicazioni sulla durata dell'attesa. | L'utente viene informato che il caricamento dei dati è in corso, ma non vi è alcuna indicazione della durata dell'attesa. | Nessun caricamento di dati o indicatori di processo per l'attività che richiede più di 5 secondi. |

### <a name="how-to-measure"></a>Come misurare

* Durante il caricamento dei dati verificare che non ci sia stato vuoto per più di 5 secondi.

### <a name="recommendations"></a>Consigli

* Fornire un animatore di caricamento dei dati che mostri lo stato di avanzamento in qualsiasi situazione in cui l'utente potrebbe aver percepito questa app come bloccata o bloccata. Una regola generale ragionevole è qualsiasi attività di "caricamento" che potrebbe richiedere più di 5 secondi.

### <a name="resources"></a>Risorse

* [Visualizzazione dello stato](../../design/progress.md)