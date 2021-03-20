---
title: DiagnosticsSystemGettingStarted
description: documentazione per abilitare e disabilitare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 184a299a2a711aa791055856ab668583df3881b2
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684264"
---
# <a name="diagnostic-system"></a>Sistema di diagnostica

Il sistema di diagnostica del Toolkit di realtà mista fornisce strumenti di diagnostica che vengono eseguiti all'interno dell'applicazione per consentire l'analisi dei problemi dell'applicazione.

Il primo rilascio del sistema di diagnostica contiene il [Profiler visivo](UsingVisualProfiler.md) che consente di analizzare i problemi di prestazioni durante l'uso dell'applicazione.

## <a name="getting-started"></a>Introduzione

> [!IMPORTANT]
> È consigliabile **_che_** il sistema di diagnostica sia abilitato nell'intero ciclo di sviluppo del prodotto e sia disabilitato come Ultima modifica prima della compilazione e del rilascio della versione finale.

Per iniziare a usare il sistema di diagnostica, è necessario eseguire due passaggi principali.

1. [Abilitare](#enable-diagnostics) il sistema di diagnostica
2. [Configurare](#configure-diagnostic-options) le opzioni di diagnostica

### <a name="enable-diagnostics"></a>Abilitare la diagnostica

Il sistema di diagnostica è gestito dall'oggetto MixedRealityToolkit (o da un altro componente di [registrazione del servizio](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).

I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar di servizi potrebbero essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../Images/MRTK_ConfiguredHierarchy.png)

1. Passare al pannello di controllo nella sezione del sistema di diagnostica e selezionare Abilita.

    ![Abilitare il sistema di diagnostica](../Images/Diagnostics/MRTKConfig_Diagnostics.png)

1. Selezionare l'implementazione del sistema di diagnostica

    ![Selezionare l'implementazione del sistema di diagnostica](../Images/Diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> Gli utenti del profilo predefinito, `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles), avranno il sistema di diagnostica preconfigurato per l'uso dell' [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) oggetto.

### <a name="configure-diagnostic-options"></a>Configurare le opzioni di diagnostica

Il sistema di diagnostica utilizza un profilo di configurazione per specificare i componenti da visualizzare e per configurarne le impostazioni. Per ulteriori informazioni relative alle impostazioni del componente disponibili, vedere [configurazione del sistema di diagnostica](ConfiguringDiagnostics.md) .

![Opzioni di diagnostica](../Images/Diagnostics/DiagnosticsProfile.png)

> [!IMPORTANT]
> Sebbene sia possibile usare la modalità di riproduzione di Unity durante lo sviluppo di applicazioni senza la necessità di eseguire la procedura di compilazione e distribuzione, è importante valutare i risultati del sistema di diagnostica usando un'applicazione compilata in esecuzione nell'hardware e nella piattaforma di destinazione.
>
> La diagnostica delle prestazioni, ad esempio il [Profiler visuale](UsingVisualProfiler.md), potrebbe non riflettere accuratamente le prestazioni effettive delle applicazioni quando vengono eseguite dall'interno dell'editor.

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API di diagnostica](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Configurazione del sistema di diagnostica](ConfiguringDiagnostics.md)
- [Uso di Visual Profiler](UsingVisualProfiler.md)
