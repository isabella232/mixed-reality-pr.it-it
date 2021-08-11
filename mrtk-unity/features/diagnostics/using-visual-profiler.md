---
title: Uso del profiler visivo
description: documentazione per l'uso di Visual Profiler in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 5db2094b5d7354e02a9e2f06c50e4d564ea7d8d259ce31ad5a11f49a71e27839
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190945"
---
# <a name="using-the-visual-profiler"></a>Uso del profiler visivo

VisualProfiler offre una visualizzazione in-application facile da usare delle prestazioni di un'applicazione di realtà mista. Il profiler è supportato in tutte le piattaforme Toolkit realtà mista, tra cui:

- Microsoft HoloLens (prima generazione)
- Microsoft HoloLens 2
- Visori VR immersive di Windows Mixed Reality
- OpenVR

Durante lo sviluppo di un'applicazione, concentrarsi su più parti della scena, in quanto Visual Profiler visualizza i dati relativi alla visualizzazione corrente.

> [!IMPORTANT]
> Concentrare l'attenzione su parti della scena con oggetti complessi, effetti di particelle o attività. Questi e altri fattori spesso contribuiscono alla riduzione delle prestazioni dell'applicazione e a un'esperienza utente inferiore a quella ideale.

## <a name="visual-profiler-interface"></a>Interfaccia del profiler visivo

![Interfaccia di Visual Profiler](../images/diagnostics/VisualProfiler.png)

L'interfaccia di Visual Profiler include i componenti seguenti:

- [Frequenza fotogrammi](#frame-rate)
- [Tempo di fotogramma](#frame-time)
- [Frame Graph](#frame-graph)
- [Utilizzo della memoria](#memory-utilization)

### <a name="frame-rate"></a>Frequenza dei fotogrammi

Nell'angolo superiore sinistro dell'interfaccia è presente la frequenza dei fotogrammi, misurata in fotogrammi al secondo. Per la migliore esperienza utente e il massimo comfort, questo valore deve essere il più alto possibile.

La piattaforma e la configurazione hardware specifiche avranno un ruolo significativo nella frequenza fotogrammi massima ottenibile. Alcuni valori di destinazione comuni includono:

- Microsoft HoloLens: 60
- Windows Mixed Reality Ultra: 90

> [!NOTE]
> A causa della limitazione della frequenza dei [fotogrammi HoloLens](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)quando mrc predefinito è attivo, il profiler visivo si nasconde mentre vengono acquisiti video e foto. Questa impostazione può essere sostituita nel profilo di sistema di diagnostica.

### <a name="frame-time"></a>Durata fotogramma

A destra della frequenza dei fotogrammi si trova il tempo di fotogramma, in millisecondi, impiegato per la CPU. Per ottenere la frequenza dei fotogrammi di destinazione indicata in precedenza, un'applicazione può impiegare la quantità di tempo seguente per ogni fotogramma:

- 60 fps: 16,6 ms
- 90 fps: 11,1 ms

L'ora della GPU è pianificata per essere aggiunta in una versione futura.

### <a name="frame-graph"></a>Grafico a cornice

Il grafico dei frame fornisce una visualizzazione grafica della cronologia della frequenza dei fotogrammi dell'applicazione.

![Frame persi di Visual Profiler Graph](../images/diagnostics/VisualProfilerMissedFrames.png)

Quando si usa l'applicazione, cercare i fotogrammi persi che indicano che l'applicazione non sta toccando la frequenza dei fotogrammi di destinazione e potrebbe essere necessario un lavoro di ottimizzazione.

### <a name="memory-utilization"></a>Utilizzo della memoria

La visualizzazione dell'utilizzo della memoria consente di comprendere facilmente in che modo la visualizzazione corrente influisce sul consumo di memoria di un'applicazione.

![Memoria di Visual Profiler Graph](../images/diagnostics/VisualProfilerMemory.png)

Quando si usa l'applicazione, cercare l'utilizzo totale della memoria. Gli indicatori chiave includono la prossimità del limite di memoria e i rapidi cambiamenti nell'utilizzo.

## <a name="customizing-the-visual-profiler"></a>Personalizzazione del profiler visivo

L'aspetto e il comportamento di Visual Profiler sono personalizzabili tramite il profilo di sistema di diagnostica. Per altre [informazioni, vedere Configurazione del sistema](configuring-diagnostics.md) di diagnostica.

## <a name="see-also"></a>Vedi anche

- [Sistema di diagnostica](diagnostics-system-getting-started.md)
- [Configurazione del sistema di diagnostica](configuring-diagnostics.md)
