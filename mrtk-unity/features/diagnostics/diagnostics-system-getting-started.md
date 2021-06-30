---
title: Panoramica del sistema di diagnostica
description: Documentazione per abilitare e disabilitare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0de7b904a48453d6021cf7aed5835412c19b7884
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121779"
---
# <a name="diagnostic-system"></a>Sistema di diagnostica

Mixed Reality Toolkit Diagnostic System fornisce strumenti di diagnostica eseguiti all'interno dell'applicazione per consentire l'analisi dei problemi dell'applicazione.

La prima versione del sistema di diagnostica contiene [Visual Profiler](using-visual-profiler.md) per consentire l'analisi dei problemi di prestazioni durante l'uso dell'applicazione.

## <a name="getting-started"></a>Guida introduttiva

> [!IMPORTANT]
> È **_consigliabile che_** il sistema di diagnostica sia abilitato per l'intero ciclo di sviluppo del prodotto e disabilitato come ultima modifica prima di compilare e rilasciare la versione finale.

Esistono due passaggi chiave per iniziare a usare il sistema di diagnostica.

1. [Abilitare](#enable-diagnostics) il sistema di diagnostica
2. [Configurare le](#configure-diagnostic-options) opzioni di diagnostica

### <a name="enable-diagnostics"></a>Abilitare la diagnostica

Il sistema di diagnostica è gestito dall'oggetto MixedRealityToolkit (o da un altro [componente del registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) del servizio).

La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar del servizio possono essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Passare al pannello Inspector (Controllo) nella sezione Diagnostics System (Sistema di diagnostica) e selezionare Enable (Abilita)
1. Selezionare l'implementazione del sistema di diagnostica

    ![Selezionare l'implementazione del sistema di diagnostica](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> Gli utenti del profilo predefinito `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) avranno il sistema di diagnostica preconfigurato per l'uso [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) dell'oggetto.

### <a name="configure-diagnostic-options"></a>Configurare le opzioni di diagnostica

Il sistema di diagnostica usa un profilo di configurazione per specificare i componenti da visualizzare e per configurarne le impostazioni. Per altre [informazioni relative alle impostazioni dei](configuring-diagnostics.md) componenti disponibili, vedere Configurazione del sistema di diagnostica.

> [!IMPORTANT]
> Sebbene sia possibile usare la modalità di riproduzione di Unity durante lo sviluppo di applicazioni senza richiedere i passaggi di compilazione e distribuzione, è importante valutare i risultati del sistema di diagnostica usando un'applicazione compilata in esecuzione nell'hardware e nella piattaforma di destinazione.
>
> La diagnostica delle prestazioni, ad esempio [Visual Profiler](using-visual-profiler.md), potrebbe non riflettere in modo accurato le prestazioni effettive dell'applicazione quando viene eseguita dall'editor.

## <a name="see-also"></a>Vedere anche

- [Documentazione dell'API di diagnostica](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Configurazione del sistema di diagnostica](configuring-diagnostics.md)
- [Uso di Visual Profiler](using-visual-profiler.md)
