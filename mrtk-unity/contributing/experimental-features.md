---
title: Funzionalità sperimentali
description: Documento relativo alle funzionalità sperimentali in MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 341ba0ee3e5900cc52f1ef715232f49064102309
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121379"
---
# <a name="experimental-features"></a>Funzionalità sperimentali

Alcune funzionalità a cui lavora il team di MRTK sembrano avere un valore iniziale molto grande anche se i dettagli non sono stati completamente dettagliati. Per questi tipi di funzionalità, la community vuole avere la possibilità di vederle in anticipo. Poiché sono all'inizio del ciclo, vengono etichettati come sperimentali per indicare che sono ancora in evoluzione e soggetti a modifiche nel tempo.

## <a name="what-to-expect-from-an-experimental-feature"></a>Cosa aspettarsi da una funzionalità sperimentale

Se un componente è contrassegnato come sperimentale, è possibile prevedere quanto segue:

- Scena di esempio che illustra l'utilizzo, che si trova `MRTK/Examples/Experimental` nella sottocartella
- Le funzionalità sperimentali potrebbero non avere documenti.
- Probabilmente non hanno test.
- Le funzionalità sperimentali sono soggette a modifiche.

## <a name="experimental-feature-guidelines"></a>Linee guida sulle funzionalità sperimentali

### <a name="experimental-code-should-live-in-a-separate-folder"></a>Il codice sperimentale deve essere contenuto in una cartella separata

Il codice sperimentale deve essere inserito in una cartella sperimentale di primo livello seguita dal nome della funzionalità sperimentale. Ad esempio, se si prova a fornire una nuova funzionalità FooBar, inserire il codice seguente:

- Scene di esempio, script `MRTK/Examples/Experimental/FooBar/`
- Script dei componenti, prefab `MRTK/SDK/Experimental/FooBar/`
- I controlli dei componenti passano a `MRTK/SDK/Inspectors/Experimental/FooBar`

Quando si usano sottocartelle sotto il nome della funzionalità sperimentale, provare a eseguire il mirroring della stessa struttura di cartelle di MRTK.

Ad esempio, i risolutori verrebbero sotto `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

Tenere le scene in una cartella della scena nella parte superiore: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> Si è considerato di non avere una singola cartella radice sperimentale e di inserire sperimentale in say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` . Si è deciso di aggiungere cartelle alla base per semplificare l'individuazione delle funzionalità sperimentali.

### <a name="experimental-code-should-be-in-a-special-namespace"></a>Il codice sperimentale deve essere in uno spazio dei nomi speciale

Assicurarsi che il codice sperimentale si trova in uno spazio dei nomi sperimentale corrispondente alla posizione non sperimentale. Ad esempio, se il componente fa parte dei risolutori in `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , il relativo spazio dei nomi deve essere `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .

Per [un esempio, vedere](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) questa richiesta pull.

### <a name="experimental-features-should-have-an-experimental-attribute"></a>Le funzionalità sperimentali devono avere un attributo [Sperimentale]

Aggiungere un attributo sopra uno dei campi per visualizzare una piccola finestra di dialogo nell'editor dei componenti che indica che la funzionalità è sperimentale e soggetta `[Experimental]` a modifiche significative.

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>I menu per le funzionalità sperimentali devono essere disponibili nel sottomenu "Sperimentale"

Assicurarsi che le funzionalità sperimentali siano disponibili nei sottomenu "sperimentali" quando si aggiungono comandi ai menu nell'editor. Ecco alcuni esempi:

Aggiunta di un comando di menu di primo livello:

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

Aggiunta di un menu dei componenti:

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>Documentazione

Seguire questa procedura per aggiungere la documentazione per la funzionalità sperimentale:

1. Qualsiasi documentazione per una funzionalità sperimentale deve essere in un `readme.md` file nella cartella sperimentale. Ad esempio, MRTK/SDK/Experimental/PulseShader/readme.md.

1. In *Cenni preliminari sulle* funzionalità aggiungere un collegamento nella sezione *Sperimentale* all'indirizzo [`Documentation/toc.yml`](../toc.yml) .

### <a name="minimize-impact-to-mrtk-code"></a>Ridurre al minimo l'impatto sul codice MRTK

Anche se la modifica di MRTK potrebbe far funzionare l'esperimento, potrebbe influire su altre persone in modi non previsti.
Eventuali regressioni apportate al codice principale di MRTK comportano il ripristino della richiesta pull.

Mirare a non apportare modifiche alle cartelle diverse da quelle sperimentali. Ecco un elenco di cartelle che possono avere modifiche sperimentali:

- MRTK/SDK/Sperimentale
- MRTK/SDK/Inspectors/Experimental
- MRTK/Examples/Experimental

Le modifiche all'esterno di queste cartelle devono essere trattate con attenzione. Se la funzionalità sperimentale deve includere modifiche al codice principale di MRTK, valuta la possibilità di suddividere le modifiche di MRTK in una richiesta pull separata che include test e documentazione.

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>L'uso della funzionalità sperimentale non dovrebbe influire sulla capacità degli utenti di usare i controlli di base

La maggior parte delle persone usa componenti principali dell'esperienza utente come il pulsante, ManipulationHandler e Interactable molto spesso. Probabilmente non useranno la funzionalità sperimentale se impedisce loro di usare i pulsanti.

L'uso del componente non deve interrompere i pulsanti, ManipulationHandler, BoundingBox o interagire.

Ad esempio, in questa richiesta pull [ScrollableObjectCollection,](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)l'aggiunta di un oggetto ScrollableObjectCollection ha causato la non possibilità di usare i prefab del pulsante HoloLens. Anche se questo non è stato causato da un bug nella richiesta pull (ma piuttosto da un bug esistente), ha impedito l'accesso alla richiesta pull.

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>Fornire una scena di esempio che illustra come usare la funzionalità

Gli utenti devono vedere come usare la funzionalità e come testarla.

Fornire un esempio in MRTK/Examples/Experimental/YOUR_FEATURE

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>Ridurre al minimo i difetti visibili all'utente nelle funzionalità sperimentali

Altri utenti non useranno la funzionalità sperimentale se non funziona, non rilasseranno a una funzionalità.

Testare la scena di esempio nella piattaforma di destinazione, assicurarsi che funzioni come previsto. Assicurarsi che la funzionalità funzioni anche nell'editor, in modo che gli utenti possano eseguire rapidamente l'iterazione e visualizzare la funzionalità anche se non hanno la piattaforma di destinazione.

## <a name="graduating-experimental-code-into-mrtk-code"></a>Frammentazione del codice sperimentale nel codice MRTK

Se una funzionalità finisce per essere molto utile, è consigliabile trasformarla in codice MRTK di base. A tale scopo, la funzionalità deve avere test, documentazione e una scena di esempio.

Quando si è pronti a modificare la funzionalità MRTK, creare un problema da controllare nella richiesta pull. La richiesta pull deve includere tutti gli elementi necessari per rendere questa funzionalità di base: test, documentazione e una scena di esempio che mostra l'utilizzo.

Non dimenticare inoltre di aggiornare gli spazi dei nomi per rimuovere il sottospazio "Sperimentale".
