---
title: Stabilità degli ologrammi
description: I HoloLens stabilizzano automaticamente gli ologrammi, ma gli sviluppatori possono eseguire alcuni passaggi per migliorare ulteriormente la stabilità degli ologrammi.
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: ologrammi, stabilità, hololens, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, frequenza dei fotogrammi, rendering, nuova progetto, separazione dei colori
appliesto:
- HoloLens
ms.openlocfilehash: a9a260208764db86d3a2d945cb6a1a611e66848889dfc228d9341f10b8e054ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198822"
---
# <a name="hologram-stability"></a>Stabilità degli ologrammi

Per ottenere ologrammi stabili, HoloLens dispone di una pipeline di stabilizzazione delle immagini predefinita. La pipeline di stabilizzazione funziona automaticamente in background, quindi non è necessario eseguire passaggi aggiuntivi per abilitarla. È tuttavia consigliabile fare pratica con tecniche che migliorano la stabilità degli ologrammi ed evitano scenari che riducono la stabilità.

## <a name="hologram-quality-terminology"></a>Terminologia relativa alla qualità degli ologrammi

La qualità degli ologrammi è il risultato di un ambiente valido e di un buon sviluppo di app. Le app in esecuzione a una costante di 60 fotogrammi al secondo in un ambiente in cui HoloLens può tenere traccia dell'ambiente circostante garantisce la sincronizzazione dell'ologramma e del sistema di coordinate corrispondente. Dal punto di vista dell'utente, gli ologrammi destinati a essere stazionari non vengono spostati rispetto all'ambiente.

La terminologia seguente può essere utile quando si identificano problemi con l'ambiente, frequenze di rendering incoerenti o basse o altro.
* **Precisione.** Quando l'ologramma è bloccato a livello mondiale e inserito nel mondo reale, deve rimanere nella posizione in cui è posizionato rispetto all'ambiente circostante e indipendente dal movimento dell'utente o dalle modifiche dell'ambiente di piccole dimensioni e di tipo sparse. Se in un secondo momento viene visualizzato un ologramma in una posizione imprevista, si tratta di un problema *di accuratezza.* Questi scenari possono verificarsi se due stanze distinte hanno un aspetto identico.
* **Jitter.** Gli utenti osservano l'instabilità come una vibrazione ad alta frequenza di un ologramma, che può verificarsi quando il rilevamento dell'ambiente si riduce. Per gli utenti, la soluzione esegue l'ottimizzazione [dei sensori](/hololens/hololens-updates).
* **Judder.** Frequenze di rendering basse comportano un movimento non uniforme e immagini doppie di ologrammi. Judder è particolarmente evidente negli ologrammi con movimento. Gli sviluppatori devono mantenere una [costante di 60 FPS.](hologram-stability.md#frame-rate)
* **Deriva.** Gli utenti vedono la deriva come un ologramma sembra allontanarsi dal punto in cui è stato originariamente posizionato. La deriva si verifica quando si posizionano ologrammi lontano [dagli](../../design/spatial-anchors.md)ancoraggi nello spazio, in particolare nelle parti dell'ambiente non mappate. La creazione di ologrammi vicini agli ancoraggi nello spaziale riduce la probabilità di deriva.
* **Jumpiness.** Quando un ologramma viene "espulso" o "si allontana" occasionalmente dalla posizione. Il jumpiness può verificarsi quando il rilevamento regola gli ologrammi in modo che corrispondano alla comprensione aggiornata dell'ambiente.
* **Nuotare.** Quando un ologramma sembra ondeggiare in base al movimento della testa dell'utente. La corsia si verifica quando [](hologram-stability.md#reprojection)l'applicazione non ha completamente implementato la riestrazione e se il HoloLens non è [calibrato](/hololens/hololens-calibration) per l'utente corrente. L'utente può eseguire nuovamente [l'applicazione di calibrazione](/hololens/hololens-calibration) per risolvere il problema. Gli sviluppatori possono aggiornare il piano di stabilizzazione per migliorare ulteriormente la stabilità.
* **Separazione dei colori.** I display in HoloLens sono schermi sequenziali a colori, che lampeggiano canali di colore rosso-verde-blu-verde a 60 Hz (i singoli campi di colore vengono visualizzati a 240 Hz). Ogni volta che un utente tiene traccia di un ologramma in movimento con gli occhi, i bordi iniziale e finale dell'ologramma si separano nei colori costitutivi, producendo un effetto colorante. Il grado di separazione dipende dalla velocità dell'ologramma. In alcuni casi più rari, lo spostamento di quelli con la testa veloce mentre si guarda un ologramma zionario può anche comportare un effetto di colore, denominato *[separazione dei colori.](hologram-stability.md#color-separation)*

## <a name="frame-rate"></a>Frequenza dei fotogrammi

La frequenza dei fotogrammi è il primo pilastro della stabilità degli ologrammi. Perché gli ologrammi siano stabili nel mondo, ogni immagine presentata all'utente deve avere gli ologrammi disegnati nella posizione corretta. L'oggetto viene visualizzato HoloLens 240 volte al secondo, con quattro campi di colore separati per ogni nuova immagine sottoposta a rendering, con un'esperienza utente di 60 FPS (fotogrammi al secondo). Per offrire la migliore esperienza possibile, gli sviluppatori di applicazioni devono mantenere 60 FPS, che si traduce nel fornire in modo coerente una nuova immagine al sistema operativo ogni 16 millisecondi.

**60 FPS** Per disegnare ologrammi in modo che siano posizionati nel mondo reale, HoloLens deve eseguire il rendering delle immagini dalla posizione dell'utente. Poiché il rendering delle immagini richiede tempo, HoloLens stima dove si trova la testa di un utente quando le immagini vengono visualizzate nei display. Tuttavia, questo algoritmo di stima è un'approssimazione. HoloLens hardware che regola l'immagine sottoposta a rendering per far conto della discrepanza tra la posizione stimata della testa e la posizione effettiva della testa. La regolazione fa sì che l'immagine visualizzata dall'utente venga visualizzata come se ne fosse eseguito il rendering dalla posizione corretta e che gli ologrammi siano stabili. Gli aggiornamenti dell'immagine funzionano meglio con piccole modifiche e non possono correggere completamente determinati elementi nell'immagine sottoposta a rendering, ad esempio la parallassa del movimento.

Il rendering a 60 FPS consente di eseguire tre operazioni per rendere stabili gli ologrammi:
1. Riduzione al minimo della latenza complessiva tra il rendering di un'immagine e l'immagine visualizzata dall'utente. In un motore con un gioco e un thread di rendering in esecuzione in lockstep, l'esecuzione a 30FPS può aggiungere 33,3 ms di latenza aggiuntiva. La riduzione della latenza riduce gli errori di stima e aumenta la stabilità dell'ologramma.
2. In questo modo, ogni immagine che raggiunge gli occhi dell'utente ha una quantità costante di latenza. Se si esegue il rendering a 30 fps, lo schermo visualizza ancora le immagini a 60 FPS, vale a dire che la stessa immagine verrà visualizzata due volte di seguito. Il secondo fotogramma avrà una latenza maggiore di 16,6 ms rispetto al primo fotogramma e dovrà correggere una quantità di errore più pronunciata. Questa incoerenza nella grandezza degli errori può causare un judder indesiderato di 60 Hz.
3. Riduzione dell'effetto di tremolio, caratterizzato da immagini doppie o con movimento non uniforme. Un movimento dell'ologramma più veloce e velocità di rendering inferiori determinano un effetto di tremolio più pronunciato. Impegnarsi a mantenere sempre 60 FPS consente di evitare judder per un determinato ologramma in movimento.

**Coerenza della frequenza dei fotogrammi** La coerenza della frequenza dei fotogrammi è importante quanto un numero elevato di fotogrammi al secondo. I frame eliminati occasionalmente sono inevitabili per qualsiasi applicazione con contenuto avanzato e il HoloLens implementa alcuni algoritmi sofisticati per il ripristino da anomalie occasionali. Tuttavia, una frequenza dei fotogrammi costantemente fluttuante è molto più evidente per un utente rispetto all'esecuzione coerente a frequenze di fotogrammi inferiori. Ad esempio, un'applicazione che esegue il rendering senza problemi per cinque fotogrammi (60 FPS per la durata di questi cinque fotogrammi) e quindi elimina ogni altro frame per i 10 fotogrammi successivi (30 FPS per la durata di questi 10 fotogrammi) apparirà più instabile rispetto a un'applicazione che esegue il rendering in modo coerente a 30 FPS.

In una nota correlata, il sistema operativo limitazione le applicazioni a 30 FPS quando è in esecuzione l'acquisizione [di](/hololens/holographic-photos-and-videos) realtà mista.

**Analisi delle prestazioni** Esistono diversi tipi di strumenti che possono essere usati per eseguire il benchmark della frequenza dei fotogrammi dell'applicazione, ad esempio:
* GPUView
* Debugger grafica di Visual Studio
* Profiler incorporati nei motori 3D, ad esempio Unity

## <a name="hologram-render-distances"></a>Distanze di rendering ologramma

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Il sistema visivo umano integra più segnali dipendenti dalla distanza quando si fissa e si concentra su un oggetto.
* [Consezione:](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) lo stato attivo di un singolo occhio.
* [](https://en.wikipedia.org/wiki/Convergence_(eye)) Convergenza: due occhi che si spostano verso l'interno o verso l'esterno per centrare un oggetto.
* [Visione binocolare:](https://en.wikipedia.org/wiki/Stereopsis) disparità tra le immagini dell'occhio sinistro e destro che dipendono dalla distanza di un oggetto dal punto di fissazione.
* Ombreggiatura, dimensioni angolari relative e altri segnali monografici (a occhio singolo).

La convergenza e la convergenza sono uniche perché i segnali extra-retinali correlati al modo in cui gli occhi cambiano per percepire gli oggetti a distanze diverse. Nella visualizzazione naturale, la convergenza e la convergenza sono collegate. Quando gli occhi guardano qualcosa vicino (ad esempio, il tuo occhio), gli occhi si incrociano e si adattano a un punto vicino. Quando gli occhi visualizzano qualcosa all'infinito, gli occhi diventano paralleli e l'occhio si adatta all'infinito. 

Gli utenti che HoloLens si adattano sempre a 2,0 m per mantenere un'immagine chiara perché gli schermi HoloLens sono fissi a una distanza ottico di circa 2,0 m dall'utente. Gli sviluppatori di app controllano dove convergono gli occhi degli utenti posizionando contenuto e ologrammi a varie profondità. Quando gli utenti si adattano e convergono a distanze diverse, il collegamento naturale tra i due segnali viene interrotto, il che può causare disagi visivi o affaticamenti, soprattutto quando la grandezza del conflitto è grande. 

È possibile evitare o ridurre al minimo l'impatto del conflitto tra conflitti di convergenza mantenendo il contenuto convergente il più vicino possibile a 2,0 m (ovvero, in una scena con molte profondità, le aree di interesse si avvicinano a 2,0 m, quando possibile). Quando il contenuto non può essere posizionato vicino a 2,0 m, la disaffezione dal conflitto tra conflitti di conflitto tra recinti e conflitti è maggiore quando lo sguardo dell'utente avanti e indietro tra distanze diverse. In altre parole, è molto più confortevole guardare un ologramma che rimane fisso a 50 cm di distanza rispetto a un ologramma distante 50 cm che si avvicina e si allontana gradualmente.

Anche il posizionamento del contenuto a 2,0 m è vantaggioso perché i due schermi sono progettati per sovrapporsi completamente a questa distanza. Per le immagini posizionate al di fuori di questo piano, quando si spostano dal lato della cornice olografica, verranno visualizzate da uno schermo pur rimanendo visibili sull'altro. Questa rivalità binocolare può essere dannosa per la percezione della profondità dell'ologramma.

**Distanza ottimale per il posizionamento degli ologrammi rispetto allo sguardo dell'utente**

![Distanza ottimale per il posizionamento degli ologrammi rispetto allo sguardo dell'utente](images/distanceguiderendering-750px.png)

**Piani di ritaglio** Per il massimo comfort, è consigliabile ritagliare la distanza di rendering a 85 cm con dissolvenza dal contenuto a partire da 1 m. Nelle applicazioni in cui gli ologrammi e gli utenti sono entrambi stazionari, gli ologrammi possono essere visualizzati con un'altezza di circa 50 cm. In questi casi, le applicazioni devono posizionare un piano di ritaglio non più vicino a 30 cm e la dissolvenza in uscita deve iniziare ad almeno 10 cm di distanza dal piano di ritaglio. Ogni volta che il contenuto è più vicino a 85 cm, è importante assicurarsi che gli utenti non si spostino spesso più vicino o più lontano dagli ologrammi o che gli ologrammi non si spostino spesso più vicino o più lontano dall'utente, perché queste situazioni hanno maggiori probabilità di causare disagi a causa del conflitto tra conflitti di conflitto tra recintivi. Il contenuto deve essere progettato per ridurre al minimo la necessità di un'interazione più vicina a 85 cm dall'utente, ma quando il rendering del contenuto deve essere eseguito più di 85 cm, una buona regola generale per gli sviluppatori è quella di progettare scenari in cui gli utenti e/o gli ologrammi non si spostano in profondità più del 25% del tempo.

**Procedure consigliate** Quando gli ologrammi non possono essere posizionati a 2 m e non è possibile evitare conflitti tra convergenza e convergenza, la zona ottimale per il posizionamento degli ologrammi è compresa tra 1,25 m e 5 m. In ogni caso, i progettisti devono strutturare il contenuto per incoraggiare gli utenti a interagire a una distanza di oltre 1 m (ad esempio, modificare le dimensioni del contenuto e i parametri di posizionamento predefiniti).

## <a name="reprojection"></a>Riproiezione
HoloLens ha una sofisticata tecnica di stabilizzazione olografica assistita da hardware nota come reproiezione. La riproiezione prende in considerazione il movimento e il cambiamento del punto di vista (CameraPose) mentre la scena viene animata e l'utente sposta la testa.  Le applicazioni devono eseguire azioni specifiche per usare al meglio la riproiezione.


Esistono quattro tipi principali di riproiezione
* **Riprogettazione della profondità:**  Produce i risultati migliori con il minor impegno dell'applicazione.  Tutte le parti della scena sottoposta a rendering vengono stabilizzate in modo indipendente in base alla distanza dall'utente.  Alcuni elementi di rendering possono essere visibili in caso di modifiche approfondite.  Questa opzione è disponibile solo per i visori HoloLens 2 visori immersivi e immersivi.
* **Riprogettazione planare:**  Consente all'applicazione un controllo preciso sulla stabilizzazione.  Un piano viene impostato dall'applicazione e tutti gli elementi su tale piano saranno la parte più stabile della scena.  Più un ologramma è lontano dal piano, meno stabile sarà.  Questa opzione è disponibile in tutte le Windows MR.
* **Riprogettazione planare automatica:**  Il sistema imposta un piano di stabilizzazione usando le informazioni nel buffer di profondità.  Questa opzione è disponibile in HoloLens generazione 1 e HoloLens 2.
* **Nessuno:** Se l'applicazione non esegue alcuna operazione, la riproiezione planare viene usata con il piano di stabilizzazione fisso a 2 metri nella direzione dello sguardo della testa dell'utente, producendo in genere risultati non standard.

Le applicazioni devono eseguire azioni specifiche per abilitare i diversi tipi di riproiezione
* **Riprogettazione della profondità:** L'applicazione invia il buffer di profondità al sistema per ogni frame sottoposto a rendering.  In Unity la riproiezione della profondità viene eseguita con l'opzione **Shared Depth Buffer** **nel** riquadro Windows Mixed Reality Impostazioni in **Gestione plug-in XR.**  Le app DirectX chiamano CommitDirect3D11DepthBuffer.  L'applicazione non deve chiamare SetFocusPoint.
* **Riprogettazione planare:** In ogni fotogramma, le applicazioni specificano al sistema la posizione di un piano da stabilizzare.  Le applicazioni Unity chiamano SetFocusPointForFrame e devono avere **shared depth buffer disabilitato.**  Le app DirectX chiamano SetFocusPoint e non devono chiamare CommitDirect3D11DepthBuffer.
* **Riprogettazione planare automatica:** Per abilitarla, l'applicazione deve inviare il buffer di profondità al sistema come per la riproiezione della profondità. Le app che usano mixed reality Toolkit (MRTK) possono configurare il provider di impostazioni della [fotocamera](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) per l'uso della riproiezione autoplanare. Le app native devono impostare `DepthReprojectionMode` in [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) su `AutoPlanar` ogni frame. Per HoloLens generazione 1, l'applicazione non deve chiamare SetFocusPoint.

### <a name="choosing-reprojection-technique"></a>Scelta della tecnica di riproiezione

Tipo di stabilizzazione |    Visori immersivi |    HoloLens generazione 1 | HoloLens 2
--- | --- | --- | ---
Riprogettazione della profondità |    Consigliato |   N/D |   Consigliato<br/><br/>Le applicazioni Unity devono usare Unity 2018.4.12+, Unity 2019.3+ o Unity 2020.3+. In caso contrario, usare la riproiezione planare automatica.
Riprogettazione planare automatica | N/D |   Impostazione predefinita consigliata |   Consigliato se la riproiezione della profondità non dà i risultati migliori<br/><br/>Per le applicazioni Unity è consigliabile usare Unity 2018.4.12+, Unity 2019.3+ o Unity 2020.3+.  Le versioni precedenti di Unity funzioneranno con risultati di riproiezione leggermente danneggiati.
Riprogettazione planare |   Non consigliato |   Consigliato se l'opzione Planar automatico non dà i risultati migliori | Usare se nessuna delle opzioni di profondità consente di ottenere i risultati desiderati    

### <a name="verifying-depth-is-set-correctly"></a>Verifica della corretta impostazione della profondità
            
Quando un metodo di riproiezione usa il buffer di profondità, è importante verificare il contenuto del buffer di profondità che rappresenta la scena sottoposta a rendering dell'applicazione.  Diversi fattori possono causare problemi. Se è presente una seconda fotocamera usata per eseguire il rendering delle sovrapposizioni dell'interfaccia utente, ad esempio, è probabile che sovrascriva tutte le informazioni sulla profondità dalla visualizzazione effettiva.  Gli oggetti trasparenti spesso non impostano la profondità.  Per impostazione predefinita, il rendering del testo non imposta la profondità.  Nel rendering saranno presenti problemi visibili quando la profondità non corrisponde agli ologrammi sottoposti a rendering.
            
HoloLens 2 un visualizzatore per mostrare dove la profondità è e non è impostata, che può essere abilitata da Portale di dispositivi.  Nella scheda **Views**  >  **Hologram Stability (Stabilità ologramma** visualizzazioni) selezionare la casella di controllo Display depth visualization in headset (Visualizza visualizzazione **profondità nel visore).**  Le aree con profondità impostata correttamente saranno blu.  Gli elementi sottoposti a rendering che non hanno un set di profondità sono contrassegnati in rosso e devono essere fissi.  

> [!NOTE]
> La visualizzazione della profondità non verrà mostrata in Acquisizione realtà mista.  È visibile solo tramite il dispositivo.
            
Alcuni strumenti di visualizzazione GPU consentiranno la visualizzazione del buffer di profondità.  Gli sviluppatori di applicazioni possono usare questi strumenti per assicurarsi che la profondità venga impostata correttamente.  Consultare la documentazione per gli strumenti dell'applicazione.

### <a name="using-planar-reprojection"></a>Uso della riproiezione planare
> [!NOTE]
> Per i visori immersivi desktop, l'impostazione di un piano di stabilizzazione è in genere controproducente, perché offre una qualità visiva inferiore rispetto a fornire il buffer di profondità dell'app al sistema per abilitare la riproiezione basata sulla profondità per pixel. A meno che non sia in HoloLens, in genere è consigliabile evitare di impostare il piano di stabilizzazione.

![Piano di stabilizzazione per oggetti 3D](images/stab-plane-500px.jpg)

Il dispositivo tenterà automaticamente di scegliere questo piano, ma l'applicazione dovrebbe assistervi selezionando il punto di messa a fuoco nella scena. Le app Unity in esecuzione HoloLens scegliere il punto di messa a fuoco migliore in base alla scena e passarlo a [SetFocusPoint().](../unity/focus-point-in-unity.md) Un esempio di impostazione del punto attivo in DirectX è incluso nel modello di cubo di rotazione predefinito.

Unity invierà il buffer di profondità a Windows per abilitare la riproiezione per pixel quando si esegue l'app in un visore immersivo connesso a un PC desktop, che offre una qualità dell'immagine ancora migliore senza lavoro esplicito da parte dell'app. È consigliabile fornire un punto di messa a fuoco solo quando l'app è in esecuzione in un HoloLens oppure la riproiezione per pixel verrà sostituita.


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

Il posizionamento del punto di messa a fuoco dipende in gran parte da ciò che l'ologramma sta osservando. L'app ha il vettore di riferimento dello sguardo fisso e la finestra di progettazione dell'app conosce il contenuto che l'utente deve osservare.

L'unica cosa più importante che uno sviluppatore può fare per stabilizzare gli ologrammi è il rendering a 60 FPS. Scendendo al di sotto di 60 FPS si ridurrà notevolmente la stabilità dell'ologramma, indipendentemente dall'ottimizzazione del piano di stabilizzazione.

**Procedure consigliate** Non esiste un modo universale per configurare il piano di stabilizzazione ed è specifico dell'app. È consigliabile sperimentare e vedere cosa funziona meglio per il proprio scenario. Tuttavia, provare ad allineare il piano di stabilizzazione con il maggior contenuto possibile perché tutto il contenuto su questo piano è perfettamente stabilizzato.

Ad esempio:
* Se si ha solo contenuto planare (app di lettura, app per la riproduzione di video), allineare il piano di stabilizzazione al piano con il contenuto.
* Se sono presenti tre piccole sfera bloccate in tutto il mondo, rendere il piano di stabilizzazione "tagliato" anche se i centri di tutte le sphere che sono attualmente nella visualizzazione dell'utente.
* Se la scena ha contenuto a profondità sostanzialmente diverse, favorire altri oggetti.
* Assicurarsi di regolare il punto di stabilizzazione ogni fotogramma in modo che coincida con l'ologramma che l'utente sta osservando

**Elementi da evitare** Il piano di stabilizzazione è un ottimo strumento per ottenere ologrammi stabili, ma se usato in modo improprio può causare una grave instabilità dell'immagine.
* Non "licenziare e dimenticare". È possibile terminare con il piano di stabilizzazione dietro l'utente o collegato a un oggetto che non è più nella visualizzazione dell'utente. Assicurarsi che la normalità del piano di stabilizzazione sia impostata in avanti opposta alla fotocamera (ad esempio, -camera.forward)
* Non modificare rapidamente il piano di stabilizzazione tra estremi
* Non lasciare il piano di stabilizzazione impostato su una distanza/orientamento fisso
* Non consentire al piano di stabilizzazione di tagliare l'utente
* Non impostare il punto di attivazione quando si esegue in un PC desktop anziché in un HoloLens e si basano invece sulla riproiezione basata sulla profondità per pixel.

## <a name="color-separation"></a>Separazione dei colori 

A causa della natura delle HoloLens, talvolta può essere percepito un artefatto denominato "separazione dei colori". Si manifesta come l'immagine che separa in singoli colori di base: rosso, verde e blu. L'artefatto può essere particolarmente visibile quando si visualizzano oggetti bianchi, poiché hanno grandi quantità di rosso, verde e blu. È più pronunciato quando un utente tiene traccia visivamente di un ologramma che si sposta attraverso il frame olografico ad alta velocità. Un altro modo in cui l'artefatto può manifestarsi è la deformazioni/deformazioni degli oggetti. Se un oggetto ha un contrasto elevato e/o colori puri, ad esempio rosso, verde, blu, la separazione dei colori verrà percepita come una differenza di parti diverse dell'oggetto.

**Esempio dell'aspetto della separazione dei colori di un cursore arrotondato bianco bloccato dalla testa quando un utente ruota la testa a lato:**

![Esempio dell'aspetto della separazione dei colori di un cursore arrotondato bianco bloccato dalla testa quando un utente ruota la testa verso il lato.](images/colorseparationofroundwhitecursor-300px.png)

Anche se è difficile evitare completamente la separazione dei colori, sono disponibili diverse tecniche per attenuarla.

**La separazione dei colori può essere osservata in:**
* Oggetti che si spostano rapidamente, inclusi gli oggetti bloccati con la testa, ad esempio il [cursore](../../design/cursors.md).
* Oggetti sostanzialmente lontano dal piano [di stabilizzazione.](hologram-stability.md#reprojection)

**Per attenuare gli effetti della separazione dei colori:**
* Impostare l'oggetto come ritardo dello sguardo dell'utente. Dovrebbe apparire come se presentasse un'inerzia e fosse collegata al sguardo fisso "on affezionato". Questo approccio rallenta il cursore (riducendo la distanza di separazione) e lo posiziona dietro il probabile punto di sguardo fisso dell'utente. Finché si raggiunge rapidamente quando l'utente smette di spostare lo sguardo, sembra naturale.
* Se si vuole spostare un ologramma, provare a mantenere la velocità di movimento al di sotto di 5 gradi al secondo se si prevede che l'utente lo segua con gli occhi.
* Usare *la luce* anziché la *geometria* per il cursore. Un'origine di illuminazione virtuale collegata al sguardo fisso verrà percepita come un puntatore interattivo, ma non causerà la separazione dei colori.
* Regolare il piano di stabilizzazione in modo che corrisponda agli ologrammi che l'utente sta guardando.
* Rendere l'oggetto rosso, verde o blu.
* Passare a una versione sfocata del contenuto. Ad esempio, un cursore bianco rotondo può essere modificato in una linea leggermente sfocata orientata nella direzione del movimento.

Come in precedenza, il rendering a 60 FPS e l'impostazione del piano di stabilizzazione sono le tecniche più importanti per la stabilità degli ologrammi. Se si verifica una notevole separazione dei colori, assicurarsi prima di tutto che la frequenza dei fotogrammi soddisfi le aspettative.

## <a name="see-also"></a>Vedi anche
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Colore, luce e materiali](../../design/color-light-and-materials.md)
* [Interazioni istintive](../../design/interaction-fundamentals.md)
* [Stabilizzazione dell'ologramma MRTK](/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization)