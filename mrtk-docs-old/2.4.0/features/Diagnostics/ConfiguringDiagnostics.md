---
title: ConfiguringDiagnostics
description: documentazione per configurare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: bc84ab193d3c3233f2930dc955d8293af578348b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688161"
---
# <a name="configuring-the-diagnostics-system"></a>Configurazione del sistema di diagnostica

## <a name="general-settings"></a>Impostazioni generali

![Impostazioni generali di diagnostica](../Images/Diagnostics/DiagnosticsGeneralSettings.png)

### <a name="show-diagnostics"></a>Visualizza diagnostica

Indica se il sistema di diagnostica deve visualizzare o meno le opzioni di diagnostica configurate.

Quando questa opzione è disabilitata, tutte le opzioni di diagnostica configurate saranno nascoste.

## <a name="profiler-settings"></a>Impostazioni del profiler

![Impostazioni del profiler di diagnostica](../Images/Diagnostics/DiagnosticsProfilerSettings.png)

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

- [Sistema di diagnostica](DiagnosticsSystemGettingStarted.md)
- [Uso di Visual Profiler](UsingVisualProfiler.md)
