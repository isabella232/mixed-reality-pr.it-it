---
title: OptimizeWindow
description: Finestra di ottimizzazione della documentazione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 3607704ad0d1f7ecb48702335f636aa4a5f83452b0fb753d42e6e37390250238
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193803"
---
# <a name="optimize-window"></a>Finestra Ottimizza

MrTK Optimize Window è un'utilità che consente di automatizzare e informare nel processo di configurazione di un progetto di realtà mista per ottenere [prestazioni ottimali](../../performance/perf-getting-started.md) in Unity. Questo strumento si concentra in genere sulle configurazioni di rendering che, se impostate sul set di impostazioni corretto, possono risparmiare millisecondi di elaborazione.

La *destinazione di compilazione attiva* è la piattaforma di compilazione attualmente [destinata](https://docs.unity3d.com/Manual/BuildSettings.html) al progetto per la compilazione.

Destinazione *prestazioni* indica lo strumento di ottimizzazione sul tipo di endpoint del dispositivo di destinazione.

- *I visori AR* sono dispositivi di classe mobile, ad esempio HoloLens
- *I dispositivi vr autonomi* sono dispositivi di classe mobile, ad esempio Oculus Go o Quest
- *Vr Tethered* sono dispositivi basati su PC, ad esempio Samsung Odyssey, Oculus Rift o HTC Vive e così via.

![Destinazione prestazioni finestra ottimizzazione MRTK](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>Impostazione delle ottimizzazioni

La scheda ottimizzazione delle impostazioni illustra alcune delle importanti configurazioni di rendering per un progetto Unity. Questa sezione consente di automatizzare e informare l'utente delle impostazioni da modificare per ottenere risultati ottimali.

Un'icona di controllo verde indica che è stato configurato un valore ottimale nel progetto/scena per questa particolare impostazione. Un'icona di avviso gialla indica che è possibile migliorare la configurazione corrente. Facendo clic sul pulsante associato in una determinata sezione, l'impostazione nel progetto/scena unity verrà configurata automaticamente su un valore più ottimale.

![Finestra di ottimizzazione MRTK Impostazioni](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>Rendering con istanza a passaggio singolo

[Il rendering con istanze a passaggio](https://docs.unity3d.com/Manual/SinglePassInstancing.html) singolo è il percorso di rendering più efficiente per le applicazioni di realtà mista. Questa configurazione garantisce che la pipeline di rendering sia eseguita una sola volta per entrambi gli occhi e che le chiamate di disegno siano eseguite su entrambi gli occhi.

### <a name="depth-buffer-sharing"></a>Condivisione buffer di profondità

Per migliorare [la stabilizzazione degli ologrammi,](../../performance/hologram-Stabilization.md)gli sviluppatori possono condividere il buffer di profondità dell'applicazione, che fornisce alla piattaforma informazioni su dove e quali ologrammi stabilizzarsi nella scena sottoposta a rendering.

### <a name="depth-buffer-format"></a>Formato del buffer di profondità

Inoltre, per *i visori AR,* è consigliabile usare un formato di profondità a 16 bit quando si abilita la condivisione del buffer di profondità rispetto a 24 bit. Ciò significa una precisione inferiore, ma consente di risparmiare sulle prestazioni. Se lo [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) si verifica perché il calcolo della profondità per i pixel è inferiore, è consigliabile spostare il piano di [ritaglio](https://docs.unity3d.com/Manual/class-Camera.html) lontano più vicino alla fotocamera (ad esempio, 50 m anziché 1000 m).

> [!NOTE]
> Se si usa un formato di profondità a *16 bit,* gli effetti necessari per il buffer di stencil non funzioneranno perché Unity non crea un [buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il formato di profondità a *24 bit,* in genere verrà creato un buffer di stencil a [8 bit,](https://docs.unity3d.com/Manual/SL-Stencil.html)se applicabile nella piattaforma grafica dell'endpoint.
>
> Se si usa un componente [Mask](https://docs.unity3d.com/Manual/script-Mask.html) che richiede il buffer di stencil, prendere in considerazione l'uso di [RectMask2D,](https://docs.unity3d.com/Manual/script-RectMask2D.html) che non richiede il buffer di stencil e quindi può essere usato in combinazione con un formato di profondità a *16 bit.*

### <a name="real-time-global-illumination"></a>Illuminazione globale in tempo reale

[L'illuminazione globale](https://docs.unity3d.com/Manual/GIIntro.html) in tempo reale in Unity può offrire risultati estetici straordinari, ma a un costo molto elevato. L'illuminazione globale è molto costosa nella realtà mista ed è quindi consigliabile disabilitare questa funzionalità in fase di sviluppo.

> [!NOTE]
> Le impostazioni di illuminazione globali in Unity vengono impostate per scena e non una sola volta nell'intero progetto.

## <a name="scene-analysis"></a>Analisi della scena

La *scheda Analisi* della scena è progettata per informare gli sviluppatori sugli elementi attualmente presenti nella scena che avranno probabilmente l'impatto maggiore sulle prestazioni.

![MrTK Optimize Window Impostazioni scene Analysis (Analisi della scena di ottimizzazione Impostazioni MRTK)](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>Analisi dell'illuminazione

Questa sezione esaminerà il numero di luci attualmente presenti nella scena, nonché tutte le luci che devono disabilitare le ombreggiature. Il cast di ombreggiatura è un'operazione molto costosa.

### <a name="polygon-count-analysis"></a>Analisi del numero di poligoni

Lo strumento fornisce anche statistiche sul conteggio dei poligoni. Può essere molto utile identificare rapidamente gli oggetti GameObject con la complessità poligonale più elevata in una determinata scena da usare come destinazione per le ottimizzazioni.

### <a name="unity-ui-raycast-analysis"></a>Analisi raycast dell'interfaccia utente di Unity

Le operazioni di raycast della grafica vengono eseguite per ogni puntatore in MRTK per determinare se gli elementi dell'interfaccia utente di Unity sono nello stato attivo. Questi raycast possono essere piuttosto costosi e per migliorare le prestazioni, gli elementi dell'interfaccia utente che non devono essere restituiti nei risultati devono essere disabilitati come destinazioni raycast. Ogni [elemento Graphic](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) ha una proprietà [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) . Questo strumento cerca gli elementi dell'interfaccia utente di testo con questa proprietà abilitata e pertanto è probabile che i candidati siano disabilitati.

## <a name="shader-analysis"></a>Analisi dello shader

Lo [shader Unity Standard](https://docs.unity3d.com/Manual/shader-StandardShader.html) può produrre risultati visivi di qualità molto elevata per i giochi, ma non è in genere più adatto alle esigenze di prestazioni delle applicazioni di realtà mista, soprattutto perché tali applicazioni sono in genere vincolate da GPU. È quindi consigliabile agli sviluppatori usare lo [shader STANDARD MRTK](../rendering/mrtk-standard-shader.md) per bilanciare l'& delle funzionalità grafiche con le prestazioni.

La *scheda Analisi* shader analizza la cartella Asset del progetto corrente per i materiali usando lo shader Unity Standard o, se lo si desidera, tutti i materiali che non usano realtà mista Toolkit shader forniti. Una volta individuati, gli sviluppatori possono convertire tutti i materiali o singolarmente usando i pulsanti appropriati.

![Ottimizzazione della finestra MRTK Impostazioni'analisi shader](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>Vedere anche

- [Prestazioni](../../performance/perf-getting-started.md)
- [Stabilizzazione dell'ologramma](../../performance/hologram-stabilization.md)
