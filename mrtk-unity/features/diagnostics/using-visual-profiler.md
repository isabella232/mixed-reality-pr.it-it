---
title: Uso di Visual Profiler
description: documentazione per l'uso di Visual Profiler in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4830615fd55a39614dd775dd7628938ee3af1c3b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143710"
---
# <a name="using-the-visual-profiler"></a>Uso del profiler visivo

VisualProfiler offre una visualizzazione in-application facile da usare delle prestazioni di un'applicazione di realtà mista. Il profiler è supportato in tutte le piattaforme mixed reality toolkit, tra cui:

- Microsoft HoloLens (prima generazione)
- Microsoft HoloLens 2
- Visori VR immersive di Windows Mixed Reality
- OpenVR

Durante lo sviluppo di un'applicazione, concentrarsi su più parti della scena quando Visual Profiler visualizza i dati relativi alla visualizzazione corrente.

> [!IMPORTANT]
> Concentrare l'attenzione su parti della scena con oggetti complessi, effetti di particelle o attività. Questi e altri fattori contribuiscono spesso alla riduzione delle prestazioni dell'applicazione e a un'esperienza utente inferiore a quella ideale.

## <a name="visual-profiler-interface"></a>Interfaccia del profiler visivo

![Interfaccia di Visual Profiler](../images/diagnostics/VisualProfiler.png)

L'interfaccia di Visual Profiler include i componenti seguenti:

- [Frequenza dei fotogrammi](#frame-rate)
- [Tempo dell'intervallo](#frame-time)
- [Grafico dei frame](#frame-graph)
- [Utilizzo della memoria](#memory-utilization)

### <a name="frame-rate"></a>Frequenza dei fotogrammi

Nell'angolo superiore sinistro dell'interfaccia è presente la frequenza dei fotogrammi, misurata in fotogrammi al secondo. Per la migliore esperienza utente e il massimo comfort, questo valore deve essere il più alto possibile.

La piattaforma e la configurazione hardware specifiche avranno un ruolo significativo nella frequenza dei fotogrammi massima ottenibile. Alcuni valori di destinazione comuni includono:

- Microsoft HoloLens: 60
- Windows Mixed Reality Ultra: 90

> [!NOTE]
> A causa della limitazione della frequenza dei fotogrammi in [HoloLens](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)quando mrC predefinito è attivo, il profiler visivo si nasconde mentre vengono acquisiti video e foto. Questa impostazione può essere sostituita nel profilo di sistema di diagnostica.

### <a name="frame-time"></a>Durata fotogramma

A destra della frequenza dei fotogrammi si trova il tempo di fotogramma, in millisecondi, impiegato per la CPU. Per ottenere la frequenza dei fotogrammi di destinazione indicata in precedenza, un'applicazione può impiegare la quantità di tempo seguente per ogni fotogramma:

- 60 fps: 16,6 ms
- 90 fps: 11,1 ms

L'ora della GPU è pianificata per essere aggiunta in una versione futura.

### <a name="frame-graph"></a>Grafico a cornice

Il grafico dei frame fornisce una visualizzazione grafica della cronologia della frequenza dei fotogrammi dell'applicazione.

![Grafico dei fotogrammi persi di Visual Profiler](../images/diagnostics/VisualProfilerMissedFrames.png)

Quando si usa l'applicazione, cercare i fotogrammi persi che indicano che l'applicazione non sta toccando la frequenza dei fotogrammi di destinazione e potrebbe essere necessaria un'operazione di ottimizzazione.

### <a name="memory-utilization"></a>Utilizzo della memoria

La visualizzazione dell'utilizzo della memoria consente di comprendere facilmente in che modo la visualizzazione corrente influisce sul consumo di memoria di un'applicazione.

![Grafico della memoria di Visual Profiler](../images/diagnostics/VisualProfilerMemory.png)

Quando si usa l'applicazione, cercare l'utilizzo totale della memoria. Gli indicatori chiave includono la prossimità del limite di memoria e i rapidi cambiamenti nell'utilizzo.

## <a name="customizing-the-visual-profiler"></a>Personalizzazione del profiler visivo

L'aspetto e il comportamento di Visual Profiler sono personalizzabili tramite il profilo di sistema di diagnostica. Per altre [informazioni, vedere Configurazione del sistema](configuring-diagnostics.md) di diagnostica.

## <a name="see-also"></a>Vedi anche

- [Sistema di diagnostica](diagnostics-system-getting-started.md)
- [Configurazione del sistema di diagnostica](configuring-diagnostics.md)