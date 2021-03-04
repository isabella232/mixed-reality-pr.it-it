---
title: UsingVisualProfiler
description: documentazione per l'uso di Visual Profiler in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7bfba084f59f5b345a60d53360eaade283b9730a
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783577"
---
# <a name="using-the-visual-profiler"></a>Uso di Visual Profiler

Il VisualProfiler offre una visualizzazione di facile utilizzo, in applicazioni, delle prestazioni di un'applicazione di realtà mista. Il profiler è supportato in tutte le piattaforme Toolkit per realtà miste, tra cui:

- Microsoft HoloLens (1a generazione)
- Microsoft HoloLens 2
- Visori VR immersive di Windows Mixed Reality
- OpenVR

Durante lo sviluppo di un'applicazione, è possibile concentrarsi su più parti della scena perché Visual Profiler Visualizza i dati relativi alla visualizzazione corrente.

> [!IMPORTANT]
> Concentrare l'attenzione sulle parti della scena con oggetti complessi, effetti particellari o attività. Questi e altri fattori spesso contribuiscono a ridurre le prestazioni dell'applicazione e a un'esperienza utente inferiore a quella ideale.

## <a name="visual-profiler-interface"></a>Interfaccia di Visual Profiler

![Interfaccia di Visual Profiler](../images/diagnostics/VisualProfiler.png)

L'interfaccia di Visual Profiler include i componenti seguenti:

- [Frequenza fotogrammi](#frame-rate)
- [Tempo frame](#frame-time)
- [Grafico frame](#frame-graph)
- [Utilizzo memoria](#memory-utilization)

### <a name="frame-rate"></a>Frequenza dei fotogrammi

Nell'angolo superiore sinistro dell'interfaccia è la frequenza dei fotogrammi, misurata in fotogrammi al secondo. Per ottimizzare l'esperienza utente e la comodità, questo valore dovrebbe essere il più elevato possibile.

La piattaforma e la configurazione hardware specifiche giocheranno un ruolo significativo nella frequenza massima ottenibile di frame. Alcuni valori di destinazione comuni includono:

- Microsoft HoloLens: 60
- Realtà mista di Windows Ultra: 90

> [!NOTE]
> A causa della [limitazione delle richieste di frequenza dei fotogrammi in HoloLens quando è attiva la fase MRC predefinita](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), il Profiler visivo si nasconde mentre vengono acquisiti video e foto. È possibile eseguire l'override di questa impostazione nel profilo di sistema di diagnostica.

### <a name="frame-time"></a>Durata fotogramma

A destra della frequenza dei fotogrammi è il tempo di frame, in millisecondi, dedicato alla CPU. Per ottenere le frequenze dei frame di destinazione citate in precedenza, un'applicazione può dedicare la quantità di tempo seguente per frame:

- 60 fps: 16,6 ms
- 90 fps: 11,1 ms

Il tempo GPU è pianificato per essere aggiunto in una versione futura.

### <a name="frame-graph"></a>Grafico frame

Il grafico frame fornisce una visualizzazione grafica della cronologia della frequenza dei fotogrammi dell'applicazione.

![Grafico frame mancanti di Visual Profiler](../images/diagnostics/VisualProfilerMissedFrames.png)

Quando si usa l'applicazione, cercare i frame mancanti che indicano che l'applicazione non sta raggiungendo la frequenza dei fotogrammi di destinazione e potrebbe richiedere un lavoro di ottimizzazione.

### <a name="memory-utilization"></a>Utilizzo della memoria

La visualizzazione utilizzo memoria consente di comprendere facilmente il modo in cui la visualizzazione corrente influisca sul consumo di memoria di un'applicazione.

![Grafico della memoria di Visual Profiler](../images/diagnostics/VisualProfilerMemory.png)

Quando si usa l'applicazione, cercare l'utilizzo totale della memoria. Gli indicatori chiave sono vicini al limite di memoria e a modifiche rapide nell'utilizzo.

## <a name="customizing-the-visual-profiler"></a>Personalizzazione di Visual Profiler

L'aspetto e il comportamento di Visual Profiler sono personalizzabili tramite il profilo di sistema di diagnostica. Per ulteriori informazioni, vedere [configurazione del sistema di diagnostica](configuring-diagnostics.md) .

## <a name="see-also"></a>Vedi anche

- [Sistema di diagnostica](diagnostics-system-getting-started.md)
- [Configurazione del sistema di diagnostica](configuring-diagnostics.md)
