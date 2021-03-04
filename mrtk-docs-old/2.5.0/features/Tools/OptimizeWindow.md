---
title: OptimizeWindow
description: Finestra di ottimizzazione della documentazione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 8af8857c966b6e466c3ace29b0016829add37650
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783057"
---
# <a name="optimize-window"></a>Ottimizza finestra

La finestra di ottimizzazione di MRTK è un'utilità che consente di automatizzare e informare nel processo di configurazione di un progetto di realtà mista per ottenere [prestazioni](../../Performance/PerfGettingStarted.md) ottimali in Unity. Questo strumento è in genere incentrato sulle configurazioni di rendering che, quando impostate sul set di impostazioni corretto, possono risparmiare millisecondi di elaborazione.

La *destinazione di compilazione attiva* è la [piattaforma di compilazione attualmente destinata](https://docs.unity3d.com/Manual/BuildSettings.html) al progetto per la compilazione.

La *destinazione prestazioni* indica allo strumento di ottimizzazione il tipo di endpoint dispositivo di destinazione.

- Gli *auricolari AR* sono dispositivi di classe mobile, ad esempio HoloLens
- *VR standalone* sono dispositivi di classe mobile, ad esempio Oculus go o quest
- I dispositivi *VR con tethering* sono dispositivi basati su PC, ad esempio Samsung Odyssey, Oculus Rift o HTC vive e così via.

![Destinazione prestazioni finestra ottimizza MRTK](../Images/Performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>Impostazione delle ottimizzazioni

La scheda Ottimizzazione impostazioni illustra alcune delle configurazioni di rendering importanti per un progetto Unity. Questa sezione consente di automatizzare e informare le impostazioni da modificare per ottenere risultati ottimali.

Un'icona di segno di spunta verde indica che un valore ottimale è stato configurato nel progetto o nella scena per questa particolare impostazione. Un'icona di avviso gialla indica che è possibile migliorare la configurazione corrente. Se si fa clic sul pulsante associato in una sezione specifica, questa impostazione viene configurata automaticamente nel progetto di Unity o nella scena su un valore più ottimale.

![Impostazioni finestra ottimizza MRTK](../Images/Performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>Rendering con istanza a passaggio singolo

Il [rendering a istanza singola pass](https://docs.unity3d.com/Manual/SinglePassInstancing.html) è il percorso di rendering più efficiente per le applicazioni di realtà miste. Questa configurazione garantisce che la pipeline di rendering venga eseguita una sola volta per entrambi gli occhi e che le chiamate di disegnare siano istanze in entrambi gli occhi.

### <a name="depth-buffer-sharing"></a>Condivisione buffer di profondità

Per migliorare la [stabilizzazione dell'ologramma](../../Performance/hologram-Stabilization.md), gli sviluppatori possono condividere il buffer di profondità dell'applicazione, che fornisce le informazioni sulla piattaforma in cui e quali ologrammi stabilizzare nella scena sottoposta a rendering.

### <a name="depth-buffer-format"></a>Formato buffer profondità

Inoltre, per le *cuffie AR* è consigliabile usare un formato di profondità a 16 bit quando si Abilita la condivisione del buffer di profondità rispetto a 24 bit. Ciò significa una precisione inferiore, ma risparmia sulle prestazioni. Se si verifica un [conflitto z](https://en.wikipedia.org/wiki/Z-fighting) a causa di una minore precisione nel calcolo della profondità per i pixel, è consigliabile spostare il [piano di ritaglio](https://docs.unity3d.com/Manual/class-Camera.html) più vicino alla fotocamera (ad esempio, 50m anziché 1000).

> [!NOTE]
> Se si utilizza il *formato di profondità a 16 bit*, gli effetti necessari sul buffer dello stencil non funzioneranno perché [Unity non crea un buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il *formato di profondità a 24 bit* , in genere viene creato un [buffer di stencil a 8 bit](https://docs.unity3d.com/Manual/SL-Stencil.html), se applicabile sulla piattaforma grafica dell'endpoint.
>
> Se si utilizza un [componente mask](https://docs.unity3d.com/Manual/script-Mask.html) che richiede il buffer dello stencil, provare a utilizzare [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) , che non richiede il buffer dello stencil e pertanto può essere utilizzato in combinazione con un formato di *profondità a 16 bit*.

### <a name="real-time-global-illumination"></a>Illuminazione globale in tempo reale

L' [illuminazione globale in tempo reale](https://docs.unity3d.com/Manual/GIIntro.html) in Unity può offrire risultati estetici fantastici ma a costi molto elevati. L'illuminazione globale è molto costosa in realtà mista ed è quindi consigliabile disabilitare questa funzionalità in fase di sviluppo.

> [!NOTE]
> Le impostazioni di illuminazione globale in Unity sono impostate per scena e non una volta nell'intero progetto.

## <a name="scene-analysis"></a>Analisi della scena

La scheda *analisi della scena* è progettata per informare gli sviluppatori sugli elementi attualmente presenti nella scena che probabilmente avranno il maggior effetto sulle prestazioni.

![Impostazioni finestra ottimizza MRTK](../Images/Performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>Analisi dell'illuminazione

In questa sezione verrà esaminato il numero di spie attualmente presenti nella scena, nonché tutte le luci che dovrebbero disabilitare le ombreggiature. Il cast Shadow è un'operazione molto costosa.

### <a name="polygon-count-analysis"></a>Analisi conteggio poligoni

Lo strumento fornisce anche le statistiche relative al numero di poligoni. Può essere molto utile identificare rapidamente quali GameObject hanno la complessità del poligono più elevata in una determinata scena come destinazione per le ottimizzazioni.

### <a name="unity-ui-raycast-analysis"></a>Analisi Raycast UI Unity

Le operazioni Raycast grafiche vengono eseguite per ogni puntatore in MRTK per determinare se gli elementi dell'interfaccia utente di Unity sono in stato attivo. Questi raycasts possono essere piuttosto costosi e contribuire a migliorare le prestazioni. gli elementi dell'interfaccia utente che non devono essere restituiti nei risultati devono essere disabilitati come destinazioni raycast. Ogni elemento [grafico](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) ha una [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) Proprietà. Questo strumento cercherà gli elementi dell'interfaccia utente del testo per i quali questa proprietà è abilitata e pertanto è probabile che i candidati siano disabilitati.

## <a name="shader-analysis"></a>Analisi shader

Lo [shader standard di Unity](https://docs.unity3d.com/Manual/shader-StandardShader.html) può produrre risultati visivi di qualità molto elevata per i giochi, ma in genere non è più adatto alle esigenze di prestazioni delle applicazioni di realtà mista, soprattutto perché tali applicazioni sono in genere limitate dalla GPU. È quindi consigliabile che gli sviluppatori utilizzino lo [shader standard MRTK](../README_MRTKStandardShader.md) per bilanciare le estetiche & caratteristiche grafiche con le prestazioni.

La scheda *analisi shader* analizza la cartella asset del progetto corrente per i materiali con lo shader standard Unity o, se lo si desidera, tutti i materiali che non utilizzano il Toolkit di realtà mista fornito shader. Una volta individuati, gli sviluppatori possono convertire tutti i materiali o convertirli singolarmente usando i pulsanti appropriati.

![Impostazioni finestra ottimizza MRTK](../Images/Performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>Vedere anche

- [Prestazioni](../../Performance//PerfGettingStarted.md)
- [Stabilizzazione ologramma](../../Performance/hologram-stabilization.md)
