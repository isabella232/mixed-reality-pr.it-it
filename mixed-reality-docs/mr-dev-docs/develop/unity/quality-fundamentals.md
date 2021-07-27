---
title: Concetti fondamentali sulla qualità
description: Informazioni sui concetti fondamentali sulla qualità della progettazione di applicazioni di realtà mista.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: concetti fondamentali sulla qualità, case study, progetto, esempio, MRTK, Mixed Reality Toolkit, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: e91ea1c69aeafaafa9c9bae30af6e5a288754764
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702920"
---
# <a name="quality-fundamentals"></a>Concetti fondamentali sulla qualità

Quality Fundamentals è un HoloLens 2 app che illustra i concetti fondamentali della creazione di un'esperienza di realtà mista ottimale.  Invece di apprendere e leggere informazioni sui problemi di qualità nella realtà mista, è ora possibile sperimentare in prima persona problemi ambientali, di progettazione e di prestazioni comuni e soluzioni selezionando le opzioni disponibili nell'app.

Per scaricare e installare l'app, passare alla pagina di download dell'app:

> [!div class="nextstepaction"]
> [Concetti fondamentali sulla qualità](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![Home page dei concetti fondamentali sulla qualità](images\qf-homepage.jpg)

In questa app di esempio verranno apprese le informazioni seguenti:

>[!div class = "checklist"]
> * [Device I/O and environment (I/O](#device-io-and-environment)dispositivo e ambiente): come i fattori ambientali possono influire HoloLens prestazioni.
> * [Ancoraggi nello](#anchor-fundamentals)spazio: come allineare gli ologrammi a uno spazio fisico usando ancoraggi nello spazio.
> * [Stabilità olografica e fedeltà:](#stability-and-fidelity)esplorare le tecniche per migliorare la stabilità e la fedeltà dei Ologrammi.
> * [Nozioni fondamentali degli asset 3D:](#3d-asset-fundamentals)come ottimizzare gli asset 3D per mantenere una fedeltà visiva elevata. 

## <a name="device-io-and-environment"></a>I/O del dispositivo e ambiente

Avviare l'app Concetti fondamentali sulla qualità HoloLens. Quando viene visualizzata la home page dell'app, selezionare **Device I/O (I/O dispositivo) e Environment (Ambiente).**  Si esplorerà in che modo i HoloLens e l'ambiente circostante influiscono sul mapping spaziale, sul rilevamento e sul posizionamento degli ologrammi. 

### <a name="surfaces"></a>Superfici

Gli speculari o le superfici con finiture speculari possono confondere HoloLens sensori sulla forma dell'oggetto.  Gli oggetti riflessi sulla superficie possono essere interpretati dal dispositivo come ambiente mutevoli, causando la perdita del rilevamento del dispositivo.  Se le superfici speculari causano problemi per HoloLens, è consigliabile aggiungere uno schermo o i ciechi clonabili.

Per altre informazioni, vedere [surfaces in a space](/hololens/hololens-environment-considerations#surfaces-in-a-space) in [HoloLens environment considerations](/hololens/hololens-environment-considerations).

### <a name="lighting"></a>Luce

HoloLens prestazioni possono essere influenzate negativamente da condizioni di luce molto basse o molto luminosi.  I sensori di tracciamento HoloLens hanno bisogno di circa 500-1000 metri di luce per funzionare in modo ottimale. È possibile usare un misurametro o un'app per dispositivi mobili per misurare la quantità di luce nello spazio.

Per altre informazioni, vedere [considerazioni sull'illuminazione](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) [HoloLens'ambiente](/hololens/hololens-environment-considerations).

## <a name="anchor-fundamentals"></a>Nozioni fondamentali degli ancoraggi

Per esplorare come usare Ancoraggi nello spazio per allineare gli ologrammi a uno spazio fisico, selezionare Anchor Anchor (Ancoraggi) **nella** home page dell'app.

In questa parte dell'app verranno esaminati gli scenari utente seguenti:

>[!div class = "checklist"]
> * Cosa accade quando non viene applicato alcun ancoraggio a un oggetto.
> * Quando vengono usati più ancoraggi nello spaziale per un gruppo di oggetti.
> * Condivisione di un ancoraggio nello spazio tra più collaboratori usando un codice a qr.
> * Posizionamento dell'ancoraggio per oggetti molto grandi in uno spazio.

Per altre informazioni, vedere [Ancoraggi nello spazio nella](/windows/mixed-reality/design/spatial-anchors) documentazione [di Realtà](/windows/mixed-reality/design/spatial-anchors) mista.

## <a name="stability-and-fidelity"></a>Stabilità e fedeltà

Nella home page dell'applicazione selezionare **Stability and Fidelity (Stabilità e fedeltà)** per esplorare come migliorare la stabilità dell'ologramma.

Verranno esaminati i concetti chiave seguenti:

>[!div class = "checklist"]
> * [Frequenza dei fotogrammi](#frame-rate).
> * [Late stage reprojection (LSR)](#late-stage-reprojection-lsr).
> * [Z-fighting](#z-fighting).
> * [Anti-aliasing di](#anti-aliasing).

### <a name="frame-rate"></a>Frequenza dei fotogrammi

Per offrire la migliore esperienza possibile per gli ologrammi, gli sviluppatori di applicazioni devono mantenere 60 fotogrammi al secondo (FPS).  In questa parte dell'app passare da un'opzione di conteggio triangolare all'altra per sperimentare la differenza con diverse frequenze dei fotogrammi.

![Ottimizzazione del conteggio dei triangoli](images\qf-triangle-count-optimization.png)

Per altre informazioni, vedere [frequenza dei fotogrammi](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#frame-rate) nell'articolo [sulla stabilità degli ologrammi.](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability)

### <a name="late-stage-reprojection-lsr"></a>Riproiezione in fase tardiva (LSR)

La riproiezione viene usata per stabilizzare gli ologrammi quando gli utenti si spostano nello spazio.  Provare le diverse opzioni di progetto fornite da questa parte dell'app per vedere la differenza nella qualità degli ologrammi.

![Provare le diverse opzioni di riestrazione per sperimentare la differenza.](images\qf-lsr-modes.jpg)

Per informazioni dettagliate, vedere [la riprojection nell'articolo](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#reprojection) sulla stabilità degli [ologrammi.](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability)

### <a name="z-fighting"></a>Z-fighting

Lo Z-fighting si verifica quando l'applicazione di realtà mista non riesce a distinguere quale oggetto si trova davanti all'altro.  Si noterà uno sfarfallio degli oggetti olografici che si distondono per lo stesso valore di profondità z.  Sperimentare gli effetti dell'effetto z-fighting nell'app modificando la posizione di un oggetto olografico, in questo caso il logo su una bicicletta.

![Sperimentare z-fighting con i posizionamenti degli oggetti.](images\qf-z-fighting.jpg)

Per informazioni dettagliate su z-fighting, vedere abilitare [la condivisione del buffer](/windows/mixed-reality/develop/unity/recommended-settings-for-unity#enable-depth-buffer-sharing) di profondità nell'articolo impostazioni consigliate per [Unity.](/windows/mixed-reality/develop/unity/recommended-settings-for-unity)

### <a name="anti-aliasing"></a>Anti-aliasing

L'anti-aliasing è una tecnica usata per smussare i bordi irregolari su linee curve e diagonali negli ologrammi.  In questa parte dell'app si verificano gli effetti dell'aliasing sul testo visualizzato e sugli spoke di biciclette.  

## <a name="3d-asset-fundamentals"></a>Nozioni fondamentali degli asset 3D

Nella home page dell'applicazione selezionare **3D Asset Fundamentals** (Nozioni fondamentali sugli asset 3D) per esplorare come ottimizzare gli asset 3D per soddisfare i requisiti di frequenza dei fotogrammi mantenendo al tempo stesso un'elevata fedeltà visiva.

Verranno esaminati i concetti chiave seguenti:

>[!div class = "checklist"]
> * [Conteggio triangoli](#triangle-count).
> * [Lo shader passa](#shader-passes).
> * [Draw chiama](#draw-calls).
> * [Finale](#finale).

### <a name="triangle-count"></a>Conteggio triangoli

Selezionare il numero e la complessità dei modelli di bicicletta per sperimentare la differenza visiva in base a FPS.

![Scegliere diverse opzioni di conteggio triangoli per visualizzare gli effetti sulla frequenza dei fotogrammi.](images\qf-3d-asset-visible-triangles.jpg)

Per altre informazioni, vedere Processo [di creazione degli asset.](/windows/mixed-reality/design/asset-creation-process)

### <a name="shader-passes"></a>Passaggi dello shader

Selezionare il numero di biciclette e le diverse opzioni dello shader per sperimentare la differenza visiva in base a FPS.

![Scegliere opzioni di shader diverse per visualizzare gli effetti sulla frequenza dei fotogrammi.](images\qf-3d-asset-shader-complexity.jpg)

Per altre informazioni, vedere [Shader STANDARD MRTK.](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

### <a name="draw-calls"></a>Chiamate di disegno

Le chiamate di disegno sono chiamate a elevato utilizzo di risorse alla scheda grafica.  In questa parte dell'app è possibile sperimentare prima di tutto la differenza visiva, in quanto il numero di chiamate di disegno influisce su FPS.

![Le chiamate di disegno devono essere ottimizzate per migliorare le prestazioni.](images\qf-3d-asset-draw-calls.jpg)

Vedere [Consigli sulle prestazioni da CPU a GPU.](/windows/mixed-reality/develop/unity/performance-recommendations-for-unity#cpu-to-gpu-performance-recommendations)

### <a name="finale"></a>Finale

Qui è possibile esaminare il numero di biciclette completamente ottimizzate che possono essere visualizzate e il livello di fedeltà possibile in base alle tecniche di ottimizzazione.

![Tecniche di ottimizzazione usate.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>Passaggi successivi

Esplorare altri scenari di esempio di realtà mista:

   > [!div class="nextstepaction"]
   > [Esempi e app di funzionalità](../features-and-samples.md)