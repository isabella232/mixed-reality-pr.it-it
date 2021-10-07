---
title: Nozioni fondamentali sulla qualità
description: Informazioni sui concetti fondamentali sulla qualità della progettazione di applicazioni di realtà mista.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: concetti fondamentali sulla qualità, case study, progetto, esempio, MRTK, Realtà mista Toolkit, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 69c6a55b95937c0c6af4920f6ffe0929eebe76ee
ms.sourcegitcommit: 82f7db75d8ecc7ac89c76b0db504126cbcb8f16d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129647532"
---
# <a name="quality-fundamentals"></a>Nozioni fondamentali sulla qualità

Quality Fundamentals è un HoloLens 2 app che illustra i concetti fondamentali della creazione di un'esperienza di realtà mista ottimale.  Invece di apprendere e leggere i problemi di qualità nella realtà mista, è ora possibile sperimentare in prima persona problemi comuni di ambiente, progettazione e prestazioni e soluzioni selezionando le opzioni disponibili nell'app.

Per scaricare e installare l'app, passare alla pagina di download dell'app:

> [!div class="nextstepaction"]
> [Nozioni fondamentali sulla qualità](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![Home page di Quality Fundamentals](images\qf-homepage.jpg)

In questa app di esempio verranno apprese le informazioni seguenti:

>[!div class = "checklist"]
> * [I/O del dispositivo e ambiente:](#device-io-and-environment)in che modo i fattori ambientali possono influire HoloLens prestazioni.
> * [Ancoraggi nello spazio:](#anchor-fundamentals)come allineare gli ologrammi a uno spazio fisico usando ancoraggi spaziali.
> * [Stabilità e fedeltà olografica:](#stability-and-fidelity)esplorare le tecniche per migliorare la stabilità e la fedeltà dei Ologrammi.
> * [Nozioni fondamentali degli asset 3D:](#3d-asset-fundamentals)come ottimizzare gli asset 3D per mantenere un'elevata fedeltà visiva. 

## <a name="device-io-and-environment"></a>I/O del dispositivo e ambiente

Avviare l'app Quality Fundamentals HoloLens. Quando viene visualizzata la home page dell'app, selezionare **Device I/O and Environment (Ambiente e I/O del dispositivo).**  Verrà illustrato in che modo i sensori HoloLens e l'ambiente circostante influiscono sul mapping spaziale, sul rilevamento e sul posizionamento degli ologrammi. 

### <a name="surfaces"></a>Superfici

Gli mirror o le superfici con finiture speculari possono confondere HoloLens sensori sulla forma dell'oggetto.  Gli oggetti riflessi sulla superficie possono essere interpretati dal dispositivo come ambiente mutevoli, causando la perdita del rilevamento del dispositivo.  Se le superfici speculari causano problemi per HoloLens, valutare la possibilità di aggiungere uno schermo o tende accecabili.

Per altre informazioni, vedere [Le superfici in uno spazio in](/hololens/hololens-environment-considerations#surfaces-in-a-space) HoloLens considerazioni [sull'ambiente](/hololens/hololens-environment-considerations).

### <a name="lighting"></a>Luce

HoloLens prestazioni possono essere influenzate negativamente da condizioni di luce molto bassa o molto brillante.  I sensori di rilevamento HoloLens devono funzionare in modo ottimale con circa 500-1000 lum di luce. È possibile usare un'app per dispositivi mobili o un'app per dispositivi mobili per misurare la quantità di luce nello spazio.

Per altre informazioni, vedere [considerazioni sull'illuminazione](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) [HoloLens'ambiente](/hololens/hololens-environment-considerations).

## <a name="anchor-fundamentals"></a>Nozioni fondamentali dell'ancoraggio

Per esplorare come usare Ancoraggi nello spazio per allineare gli ologrammi a uno spazio fisico, selezionare **Ancoraggi** a fondo nella home page dell'app.

In questa parte dell'app verranno esaminati gli scenari utente seguenti:

>[!div class = "checklist"]
> * Cosa accade quando non viene applicato alcun ancoraggio a un oggetto.
> * Quando vengono usati più ancoraggi spaziali per un gruppo di oggetti.
> * Condivisione di un ancoraggio spaziale tra più collaboratori usando un codice a qr.
> * Posizionamento dell'ancoraggio per oggetti molto grandi in uno spazio.

Per altre informazioni, vedere [Ancoraggi nello spazio nella](../../design/spatial-anchors.md) documentazione [di Realtà](../../design/spatial-anchors.md) mista.

## <a name="stability-and-fidelity"></a>Stabilità e fedeltà

Nella home page dell'applicazione selezionare **Stability and Fidelity (Stabilità e Fedeltà)** per esplorare come migliorare la stabilità dell'ologramma.

Verranno esaminati i concetti chiave seguenti:

>[!div class = "checklist"]
> * [Frequenza fotogrammi](#frame-rate).
> * [Riproiezione in fase tardiva (LSR).](#late-stage-reprojection-lsr)
> * [Z-fighting](#z-fighting).
> * [Antialiasing](#anti-aliasing).

### <a name="frame-rate"></a>Frequenza dei fotogrammi

Per offrire la migliore esperienza possibile per gli ologrammi, gli sviluppatori di applicazioni devono mantenere 60 fotogrammi al secondo (FPS).  In questa parte dell'app alternare le diverse opzioni di conteggio dei triangoli per sperimentare la differenza con diverse frequenze di fotogrammi.

![Ottimizzazione del conteggio dei triangoli](images\qf-triangle-count-optimization.png)

Per altre informazioni, vedere [frame rate nell'articolo](../platform-capabilities-and-apis/hologram-stability.md#frame-rate) sulla stabilità [dell'ologramma.](../platform-capabilities-and-apis/hologram-stability.md)

### <a name="late-stage-reprojection-lsr"></a>Riprogettazione in fase tardiva (LSR)

La riproiezione viene usata per stabilizzare gli ologrammi quando gli utenti si spostano nello spazio.  Provare le diverse opzioni di riproiezione fornite da questa parte dell'app per vedere la differenza nella qualità dell'ologramma.

![Provare le diverse opzioni di riproiezione per sperimentare la differenza.](images\qf-lsr-modes.jpg)

Per informazioni dettagliate, vedere [la riproiezione nell'articolo](../platform-capabilities-and-apis/hologram-stability.md#reprojection) sulla stabilità [dell'ologramma.](../platform-capabilities-and-apis/hologram-stability.md)

### <a name="z-fighting"></a>Z-fighting

Lo Z-fighting si verifica quando l'applicazione di realtà mista non riesce a distinguere quale oggetto si trova davanti all'altro.  Si noterà uno sfarfallio degli oggetti olografici mentre lottano per lo stesso valore di profondità z.  È possibile sperimentare gli effetti dello z-fighting nell'app modificando il posizionamento di un oggetto olografico, in questo caso il logo su una bicicletta.

![Esperienza di z-fighting con il posizionamento degli oggetti.](images\qf-z-fighting.jpg)

Per informazioni dettagliate sul controllo z, vedere l'articolo abilitare la condivisione [del buffer](./recommended-settings-for-unity.md#enable-depth-buffer-sharing) di profondità nelle impostazioni consigliate [per Unity.](./recommended-settings-for-unity.md)

### <a name="anti-aliasing"></a>Antialiasing

L'anti-aliasing è una tecnica usata per smussare i bordi frastagliati su linee curve e diagonali negli ologrammi.  In questa parte dell'app si verificano gli effetti dell'aliasing sul testo visualizzato e sugli spoke delle biciclette.  

## <a name="3d-asset-fundamentals"></a>Nozioni fondamentali degli asset 3D

Nella home page dell'applicazione selezionare Nozioni fondamentali sugli asset **3D** per esplorare come ottimizzare gli asset 3D per soddisfare il requisito di frequenza dei fotogrammi mantenendo un'elevata fedeltà visiva.

Verranno esaminati i concetti chiave seguenti:

>[!div class = "checklist"]
> * [Conteggio triangoli](#triangle-count).
> * [Lo shader passa](#shader-passes).
> * [Il disegno chiama](#draw-calls).
> * [Finale](#finale).

### <a name="triangle-count"></a>Conteggio triangoli

Selezionare il numero e la complessità dei modelli di biciclette per sperimentare la differenza visiva in base a FPS.

![Scegliere diverse opzioni di conteggio triangolo per visualizzare gli effetti sulla frequenza dei fotogrammi.](images\qf-3d-asset-visible-triangles.jpg)

Per altre informazioni, vedere Processo [di creazione di asset.](../../design/asset-creation-process.md)

### <a name="shader-passes"></a>Passaggi dello shader

Selezionare il numero di biciclette e le diverse opzioni dello shader per sperimentare la differenza visiva in base a FPS.

![Scegliere opzioni shader diverse per visualizzare gli effetti sulla frequenza dei fotogrammi.](images\qf-3d-asset-shader-complexity.jpg)

Per altre informazioni, vedere [MrTK Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).

### <a name="draw-calls"></a>Chiamate di disegno

Le chiamate di disegno sono chiamate a elevato utilizzo di risorse alla scheda grafica.  In questa parte dell'app si verifica la differenza visiva, in quanto il numero di chiamate di disegno influisce su FPS.

![Le chiamate di disegno devono essere ottimizzate per migliorare le prestazioni.](images\qf-3d-asset-draw-calls.jpg)

Vedere [Consigli sulle prestazioni da CPU a GPU.](./performance-recommendations-for-unity.md#cpu-to-gpu-performance-recommendations)

### <a name="finale"></a>Finale

Qui è possibile esaminare il numero di biciclette completamente ottimizzate che possono essere visualizzate e il livello di fedeltà possibile in base alle tecniche di ottimizzazione.

![Tecniche di ottimizzazione usate.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>Passaggi successivi

Esplorare altri scenari di esempio di realtà mista:

   > [!div class="nextstepaction"]
   > [Esempi e app di funzionalità](../features-and-samples.md)