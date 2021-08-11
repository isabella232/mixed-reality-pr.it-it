---
title: Procedure consigliate per OpenXR
description: Informazioni sulle procedure consigliate per la qualità visiva, la stabilità e le prestazioni per le applicazioni OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, native, native app, motore personalizzato, middleware, procedure consigliate, prestazioni, qualità, stabilità
ms.openlocfilehash: 2cbd05417f62f7380b048f692295bbbe98ceba5bce69c4f1dae21aec812ec450
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207849"
---
# <a name="openxr-app-best-practices"></a>Procedure consigliate per le app OpenXR

È possibile vedere un esempio delle procedure consigliate riportate di seguito nel file OpenXRProgram.cpp di <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp.</a> La funzione Run() all'inizio acquisisce un tipico flusso di codice dell'app OpenXR dall'inizializzazione al ciclo di eventi e rendering.

## <a name="best-practices-for-visual-quality-and-stability"></a>Procedure consigliate per la qualità e la stabilità degli oggetti visivi

Le procedure consigliate in questa sezione descrivono come ottenere la migliore qualità visiva e stabilità in qualsiasi applicazione OpenXR.

Per altre raccomandazioni sulle prestazioni specifiche HoloLens 2, vedere la sezione [Best practices for performance on HoloLens 2](#best-practices-for-performance-on-hololens-2) riportata di seguito.

### <a name="gamma-correct-rendering"></a>Rendering corretto per gamma

È necessario assicurarsi che la pipeline di rendering sia corretta per gamma. Quando si esegue il rendering in un swapchain, il formato della visualizzazione destinazione di rendering deve corrispondere al formato swapchain. Ad esempio, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` sia per il formato swapchain che per la visualizzazione di destinazione di rendering.
Esiste un'eccezione se la pipeline di rendering dell'app esegue una conversione sRGB manuale nel codice shader. L'app deve richiedere un formato swapchain sRGB, ma usare il formato lineare per la visualizzazione di destinazione di rendering. Ad esempio, richiedere come formato swapchain, ma usare come visualizzazione di destinazione di rendering per impedire la correzione della doppia gamma del `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` `DXGI_FORMAT_B8G8R8A8_UNORM` contenuto.

### <a name="submit-depth-buffer-for-projection-layers"></a>Inviare il buffer di profondità per i livelli di proiezione

Usare sempre `XR_KHR_composition_layer_depth` l'estensione e inviare il buffer di profondità insieme al livello di proiezione quando si invia un frame a `xrEndFrame` .
L'abilitazione della riproiezione della profondità hardware HoloLens 2 migliora la stabilità dell'ologramma.

### <a name="choose-a-reasonable-depth-range"></a>Scegliere un intervallo di profondità ragionevole

Preferire un intervallo di profondità più ristretto per l'ambito del contenuto virtuale per facilitare la stabilità dell'ologramma HoloLens.
Ad esempio, l'esempio OpenXrProgram.cpp usa da 0,1 metri a 20 metri.
Usare [reversed-Z](https://developer.nvidia.com/content/depth-precision-visualized) per una risoluzione di profondità più uniforme.
In HoloLens 2, l'uso del formato di profondità preferito consente di ottenere prestazioni e frequenza dei fotogrammi migliori, anche se i buffer di profondità a 16 bit offrono una risoluzione della profondità inferiore rispetto ai buffer di profondità `DXGI_FORMAT_D16_UNORM` a 24 bit.
Seguire queste procedure consigliate per usare al meglio la risoluzione della profondità diventa più importante.

### <a name="prepare-for-different-environment-blend-modes"></a>Preparare le diverse modalità di combinazione dell'ambiente

Se l'applicazione verrà eseguita anche su visori immersivi che bloccano completamente il mondo, assicurarsi di enumerare le modalità di fusione dell'ambiente supportate usando l'API e preparare correttamente il `xrEnumerateEnvironmentBlendModes` contenuto di rendering.
Ad esempio, per un sistema con come il HoloLens, l'app deve usare trasparente come colore non crittografato, mentre per un sistema con , l'app deve eseguire il rendering di un colore opaco o di una stanza virtuale `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` in background.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Scegliere lo spazio di riferimento non associato come spazio radice dell'applicazione

Le applicazioni in genere stabiliscono uno spazio di coordinate del mondo radice per connettere visualizzazioni, azioni e ologrammi.
Usare quando l'estensione è supportata per stabilire un sistema di coordinate su scala globale, consentendo all'app di evitare una deriva ologramma indesiderata quando l'utente si sposta lontano (ad esempio, a 5 metri di distanza) da dove viene avviata `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` l'app. [](../../design/coordinate-systems.md#building-a-world-scale-experience)
Usare `XR_REFERENCE_SPACE_TYPE_LOCAL` come fallback se l'estensione dello spazio non associato non esiste.

### <a name="associate-hologram-with-spatial-anchor"></a>Associare l'ologramma all'ancoraggio spaziale

Quando si usa uno spazio di riferimento non associato, gli ologrammi posizionati direttamente in tale spazio di riferimento possono deviare mentre l'utente si sposta in stanze distanti e quindi [torna indietro.](../../design/coordinate-systems.md#building-a-world-scale-experience)
Per gli utenti di ologrammi posizionati in una posizione discreta nel mondo, creare un [ancoraggio](../../design/spatial-anchors.md#best-practices) spaziale usando la funzione di estensione e posizionare `xrCreateSpatialAnchorSpaceMSFT` l'ologramma all'origine. Questo manterà l'ologramma in modo indipendente stabile nel tempo.

### <a name="support-mixed-reality-capture"></a>Supportare l'acquisizione di realtà mista

Anche se lo schermo principale di HoloLens 2 usa la fusione dell'ambiente additivo, quando l'utente avvia l'acquisizione di realtà [mista,](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)il contenuto di rendering dell'app verrà misto con il flusso video dell'ambiente.
Per ottenere la migliore qualità visiva nei video di acquisizione di realtà mista, è meglio impostare nel livello `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` di proiezione `layerFlags` .

## <a name="best-practices-for-performance-on-hololens-2"></a>Procedure consigliate per le prestazioni in HoloLens 2

Come dispositivo mobile con supporto per la riproiezione hardware, HoloLens 2 requisiti più rigorosi per prestazioni ottimali.  Esistono diversi modi per inviare i dati di composizione, con un effetto post-elaborazione con una notevole riduzione delle prestazioni.

### <a name="select-a-swapchain-format"></a>Selezionare un formato swapchain

Enumerare sempre i formati di pixel supportati usando e scegliere il primo formato pixel di colore e profondità dal runtime supportato dall'app, perché è ciò che il runtime preferisce per ottenere prestazioni `xrEnumerateSwapchainFormats` ottimali. Si noti che HoloLens 2 e in genere è la prima `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` scelta per ottenere prestazioni di rendering `DXGI_FORMAT_D16_UNORM` migliori. Questa preferenza può essere diversa nei visori VR in esecuzione in un PC desktop, in cui i buffer di profondità a 24 bit hanno un impatto minore sulle prestazioni.
  
**Avviso di prestazioni:** L'uso di un formato diverso dal formato di colore swapchain primario comporta una post-elaborazione in fase di esecuzione, con una riduzione significativa delle prestazioni.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Eseguire il rendering con i parametri di rendering consigliati e la temporizzazione dei fotogrammi

Eseguire sempre il rendering con la larghezza/altezza di configurazione della visualizzazione consigliata ( e da ) e usare sempre l'API per eseguire una query per la posizione di visualizzazione `recommendedImageRectWidth` `recommendedImageRectHeight` `XrViewConfigurationView` consigliata, l'IMMAGINE e altri parametri di rendering prima `xrLocateViews` del rendering.
Usare sempre `XrFrameEndInfo.predictedDisplayTime` dall'ultima `xrWaitFrame` chiamata durante l'esecuzione di query per pose e viste.
Ciò consente HoloLens di regolare il rendering e ottimizzare la qualità visiva per la persona che indossa il HoloLens.

### <a name="use-a-single-projection-layer"></a>Usare un singolo livello di proiezione

HoloLens 2 potenza GPU limitata per il rendering del contenuto e un compositore hardware ottimizzato per un singolo livello di proiezione.
L'uso sempre di un singolo livello di proiezione può aiutare la frequenza dei fotogrammi, la stabilità dell'ologramma e la qualità visiva dell'applicazione.  
  
**Avviso di prestazioni:** L'invio di qualsiasi altro livello di protezione, se non un singolo livello di protezione, comporta una post-elaborazione in fase di esecuzione, con una riduzione significativa delle prestazioni.

### <a name="render-with-texture-array-and-vprt"></a>Eseguire il rendering con matrice di trame e VPRT

Crearne `xrSwapchain` uno per l'occhio sinistro e destro usando `arraySize=2` per lo swapchain di colore e uno per la profondità.
Eseguire il rendering dell'occhio sinistro nella sezione 0 e dell'occhio destro nella sezione 1.
Usare uno shader con VPRT e chiamate di disegno con istanze per il rendering stereoscopico per ridurre al minimo il carico della GPU.
Ciò consente anche all'ottimizzazione del runtime di ottenere le prestazioni migliori in HoloLens 2.
Le alternative all'uso di una matrice di trame, ad esempio il rendering a larghezza doppia o un swapchain separato per occhio, comportano una post-elaborazione di runtime, con una riduzione significativa delle prestazioni.

### <a name="avoid-quad-layers"></a>Evitare i livelli quad

Anziché inviare quattro livelli come livelli di composizione con `XrCompositionLayerQuad` , eseguire il rendering del contenuto quad direttamente nello swapchain di proiezione.

**Avviso di prestazioni:** Se si forniscono livelli aggiuntivi oltre a un singolo livello di proiezione, ad esempio i livelli quad, si avrà una post-elaborazione in fase di runtime, con una riduzione significativa delle prestazioni.