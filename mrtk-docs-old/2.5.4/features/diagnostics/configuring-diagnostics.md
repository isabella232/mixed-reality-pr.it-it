---
title: ConfiguringDiagnostics
description: documentazione per configurare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 2697d0659956e1758591d40bec628a0cd9939296
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782956"
---
# <a name="configuring-the-diagnostics-system"></a>Configurazione del sistema di diagnostica

## <a name="general-settings"></a>Impostazioni generali

![Impostazioni generali di diagnostica](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>Abilita la registrazione dettagliata

Indica se la registrazione MRTK dettagliata verrà abilitata. Il valore predefinito è false, ma può essere attivato per eseguire tracce dettagliate che consentono al team di MRTK di eseguire il debug e l'analisi dei problemi. Ad esempio, quando si segnala un problema, il fissaggio dei log del lettore Unity (dall'editor o dal lettore) può contribuire a limitare l'origine di bug e problemi.

Si noti che questa opzione è indipendente dall'abilitazione o meno del sistema di diagnostica. viene visualizzato nel sistema di diagnostica perché si tratta di un'opzione di registrazione, ma opera a un livello superiore perché influiscono sulla registrazione nell'intera codebase MRTK.

### <a name="show-diagnostics"></a>Visualizza diagnostica

Indica se il sistema di diagnostica deve visualizzare o meno le opzioni di diagnostica configurate.

Quando questa opzione è disabilitata, tutte le opzioni di diagnostica configurate saranno nascoste.

## <a name="profiler-settings"></a>Impostazioni del profiler

![Impostazioni del profiler di diagnostica](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>Mostra Profiler

Indica se il profiler deve essere visualizzato o meno.

### <a name="frame-sample-rate"></a>Frequenza di campionamento frame

Quantità di tempo, in secondi, per la raccolta dei frame per il calcolo della frequenza dei fotogrammi. L'intervallo è compreso tra 0 e 5 secondi.

### <a name="window-anchor"></a>Ancoraggio finestra

A quale parte della porta di visualizzazione deve essere ancorata la finestra del profiler. Il valore predefinito è il centro inferiore.

### <a name="window-offset"></a>Offset finestra

Offset, dal centro della porta di visualizzazione, per inserire Visual Profiler. L'offset sarà nella direzione della proprietà di *ancoraggio della finestra* .

### <a name="window-scale"></a>Scala della finestra

Moltiplicatore dimensioni applicato alla finestra del profiler. Se ad esempio si imposta il valore su 2, le dimensioni della finestra vengono raddoppiate.

### <a name="window-follow-speed"></a>Velocità di completamento finestra

Velocità di spostamento della finestra del profiler per mantenere la visibilità all'interno della porta di visualizzazione.

## <a name="programmatically-controlling-the-diagnostics-system"></a>Controllo a livello di codice del sistema di diagnostica

È anche possibile impostare la visibilità del sistema di diagnostica e del profiler in fase di esecuzione. Il codice seguente, ad esempio, nasconde il sistema di diagnostica e il profiler.

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>Vedi anche

- [Sistema di diagnostica](diagnostics-system-getting-started.md)
- [Uso di Visual Profiler](using-visual-profiler.md)
