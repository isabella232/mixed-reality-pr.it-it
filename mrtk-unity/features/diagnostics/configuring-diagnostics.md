---
title: Configurazione del sistema di diagnostica
description: Documentazione per configurare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 521ef71abd1ddf920863530a2a423c1080a135e5a404a26f1611fc14f92c2796
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198243"
---
# <a name="configuring-the-diagnostics-system"></a>Configurazione del sistema di diagnostica

## <a name="general-settings"></a>Impostazioni generali

![Diagnostica generale Impostazioni](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>Abilita la registrazione dettagliata

Indica se la registrazione MRTK dettagliata verrà abilitata o meno. Questa impostazione predefinita è false, ma può essere attivata per eseguire tracce dettagliate che consentono al team MRTK di eseguire il debug o di risolvere i problemi. Ad esempio, quando si registra un problema, collegare i log del giocatore unity (dall'editor o dal lettore) può aiutare a restringere l'origine di bug e problemi.

Si noti che questa opzione è indipendente dal fatto che il sistema di diagnostica sia abilitato o meno. Questa opzione viene visualizzata nel sistema di diagnostica perché è un'opzione di registrazione, ma in definitiva funziona a un livello superiore perché influisce sulla registrazione nell'intera codebase MRTK.

### <a name="show-diagnostics"></a>Visualizza diagnostica

Indica se il sistema di diagnostica deve visualizzare le opzioni di diagnostica configurate.

Se disabilitata, tutte le opzioni di diagnostica configurate verranno nascoste.

## <a name="profiler-settings"></a>Impostazioni del profiler

![Diagnostica profiler Impostazioni](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>Mostra profiler

Indica se visual profiler deve essere visualizzato o meno.

### <a name="frame-sample-rate"></a>Frequenza di campionamento dei fotogrammi

Quantità di tempo, in secondi, per raccogliere i fotogrammi per il calcolo della frequenza dei fotogrammi. L'intervallo è compreso tra 0 e 5 secondi.

### <a name="window-anchor"></a>Ancoraggio finestra

A quale parte della porta di visualizzazione deve essere ancorata la finestra del profiler. Il valore predefinito è Centro inferiore.

### <a name="window-offset"></a>Offset della finestra

Offset, dal centro della porta di visualizzazione, per posizionare Visual Profiler. L'offset sarà nella direzione della proprietà *Ancoraggio* finestra.

### <a name="window-scale"></a>Scalabilità della finestra

Moltiplicatore di dimensioni applicato alla finestra del profiler. Ad esempio, l'impostazione del valore su 2 raddoppierà le dimensioni della finestra.

### <a name="window-follow-speed"></a>Velocità di follow della finestra

Velocità alla quale spostare la finestra del profiler per mantenere la visibilità all'interno della porta di visualizzazione.

## <a name="programmatically-controlling-the-diagnostics-system"></a>Controllo del sistema di diagnostica a livello di codice

È anche possibile attivare o disattivare la visibilità del sistema di diagnostica e del profiler in fase di esecuzione. Ad esempio, il codice seguente nasconde il sistema di diagnostica e il profiler.

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>Vedi anche

- [Sistema di diagnostica](diagnostics-system-getting-started.md)
- [Uso di Visual Profiler](using-visual-profiler.md)
