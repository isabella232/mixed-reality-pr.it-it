---
title: ExperimentalFeatures
description: Documento relativo alle funzionalità sperimentali in MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 35d51c411e2215e0b86d6de6baf823acdc0e50d2
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693318"
---
# <a name="experimental-features"></a>Funzionalità sperimentali

Alcune funzionalità del team di MRTK sembrano avere molto valore iniziale anche se non sono stati completati i dettagli. Per questi tipi di funzionalità, è necessario che la community ottenga la possibilità di vederle presto. Poiché si trovano all'inizio del ciclo, le etichette vengono etichettate come sperimentali per indicare che sono in continua evoluzione e soggette a modifiche nel tempo.

## <a name="what-to-expect-from-an-experimental-feature"></a>Cosa aspettarsi da una funzionalità sperimentale

Se un componente è contrassegnato come sperimentale, è possibile prevedere quanto segue:

- Una scena di esempio che illustra l'utilizzo, disponibile nella `MRTK/Examples/Experimental` sottocartella
- Le funzionalità sperimentali potrebbero non avere documenti.
- Probabilmente non hanno test.
- Le funzionalità sperimentali sono soggette a modifiche.

## <a name="experimental-feature-guidelines"></a>Linee guida sulle funzionalità sperimentali

### <a name="experimental-code-should-live-in-a-separate-folder"></a>Il codice sperimentale dovrebbe risiedere in una cartella separata

Il codice sperimentale dovrebbe essere inserito in una cartella sperimentale di primo livello seguita dal nome della funzionalità sperimentale. Ad esempio, se si tenta di contribuire a una nuova funzionalità FooBar, inserire il codice seguente:

- Scene di esempio, script `MRTK/Examples/Experimental/FooBar/`
- Script dei componenti, prefabbricati `MRTK/SDK/Experimental/FooBar/`
- I controlli componente entrano in `MRTK/SDK/Inspectors/Experimental/FooBar`

Quando si usano sottocartelle sotto il nome della funzionalità sperimentale, provare a eseguire il mirroring della stessa struttura di cartelle di MRTK.

Ad esempio, i risolutori subentrano `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

Mantieni le scene in una cartella della scena nella parte superiore: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> Non è stata considerata una singola cartella radice sperimentale, ma è stato inserito un esperimento sperimentale in say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` . Abbiamo deciso di usare le cartelle alla base per semplificare l'individuazione delle funzionalità sperimentali.

### <a name="experimental-code-should-be-in-a-special-namespace"></a>Il codice sperimentale deve trovarsi in uno spazio dei nomi speciale

Verificare che il codice sperimentale si trovi in uno spazio dei nomi sperimentale che corrisponda alla posizione non sperimentale. Se, ad esempio, il componente fa parte dei risolutori in `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , il relativo spazio dei nomi deve essere `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .

Per un esempio, vedere [questa](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) richiesta pull.

### <a name="experimental-features-should-have-an-experimental-attribute"></a>Le funzionalità sperimentali devono avere un attributo [Experimental]

Aggiungere un `[Experimental]` attributo sopra uno dei campi per visualizzare una piccola finestra di dialogo nell'editor del componente che indica che la funzionalità è sperimentale e soggetta a modifiche significative.

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>I menu per le funzionalità sperimentali dovrebbero andare sotto il sottomenu "sperimentale"

Quando si aggiungono comandi ai menu nell'editor, verificare che le funzionalità sperimentali siano sottomenu "sperimentali". Ecco alcuni esempi:

Aggiunta di un comando di menu di primo livello:

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

Aggiunta di un menu componenti:

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>Documentazione

Per aggiungere la documentazione per la funzionalità sperimentale, attenersi alla procedura seguente:

1. Qualsiasi documentazione relativa a una funzionalità sperimentale dovrebbe andare in un `readme.md` file nella cartella sperimentale. Ad esempio, MRTK/SDK/Experimental/PulseShader/Leggimi. MD.

1. In *Panoramica delle funzionalità* aggiungere un collegamento nella sezione *sperimentale* all'indirizzo [`Documentation/toc.yml`](../toc.yml) .

### <a name="minimize-impact-to-mrtk-code"></a>Ridurre al minimo l'effetto sul codice MRTK

Anche se la modifica del MRTK potrebbe far funzionare l'esperimento, può influito su altri utenti in modi non previsti.
Tutte le regressioni apportate al codice MRTK Core comporteranno il ripristino della richiesta pull.

Scopo di avere zero modifiche in cartelle diverse dalle cartelle sperimentali. Di seguito è riportato un elenco di cartelle che possono avere modifiche sperimentali:

- MRTK/SDK/sperimentale
- MRTK/SDK/ispettori/sperimentale
- MRTK/esempi/sperimentale

Le modifiche al di fuori di queste cartelle devono essere trattate con molta attenzione. Se la funzionalità sperimentale deve includere modifiche al codice MRTK core, è consigliabile suddividere le modifiche apportate da MRTK in una richiesta pull separata che includa i test e la documentazione.

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>L'uso della funzionalità sperimentale non dovrebbe influito sulla capacità degli utenti di usare i controlli di base

La maggior parte degli utenti usa componenti UX di base come Button, ManipulationHandler e interagiscono molto spesso. Probabilmente non utilizzeranno la funzionalità sperimentale se impedisce l'uso di pulsanti.

L'uso del componente non dovrebbe interrompere i pulsanti, ManipulationHandler, BoundingBox o interactable.

Ad esempio, in [questa](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)richiesta pull di ScrollableObjectCollection, l'aggiunta di un ScrollableObjectCollection ha impedito agli utenti di usare i prefabbricati dei pulsanti HoloLens. Anche se ciò non è stato causato da un bug nella richiesta pull (ma è stato invece esposto un bug esistente), non è stato necessario che la richiesta pull venisse archiviata.

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>Fornire una scena di esempio in cui viene illustrato come utilizzare la funzionalità

Gli utenti devono vedere come usare la funzionalità e come testarla.

Fornire un esempio in MRTK/examples/Experimental/YOUR_FEATURE

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>Ridurre al minimo gli errori visibili per gli utenti nelle funzionalità sperimentali

Altri utenti non utilizzeranno la funzionalità sperimentale se non funziona, ma non consentirà di laurearsi a una funzionalità.

Testare la scena di esempio sulla piattaforma di destinazione e verificare che funzioni come previsto. Assicurarsi che la funzionalità funzioni anche nell'editor, in modo che gli utenti possano scorrere rapidamente e visualizzare la funzionalità anche se non dispongono della piattaforma di destinazione.

## <a name="graduating-experimental-code-into-mrtk-code"></a>Graduazione del codice sperimentale nel codice MRTK

Se una funzionalità è molto utile, è necessario configurarla nel codice MRTK principale. A tale scopo, la funzionalità deve disporre di test, documentazione e una scena di esempio.

Quando si è pronti a laureare la funzionalità MRTK, creare un problema per archiviare la richiesta pull. La richiesta pull deve includere tutti gli elementi necessari per rendere questa funzionalità di base: test, documentazione e una scena di esempio che illustra l'utilizzo.

Inoltre, non dimenticare di aggiornare gli spazi dei nomi per rimuovere il sottospazio "sperimentale".
