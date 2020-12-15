---
title: Uso di XAML con app DirectX olografiche
description: Illustra l'effetto del cambio tra visualizzazioni XAML 2D e visualizzazioni immersive nell'app DirectX e come usare in modo efficiente sia una visualizzazione XAML che una visualizzazione immersiva.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: realtà mista di Windows, UWP, gestione visualizzazione App, XAML, tastiera, procedura dettagliata, DirectX
ms.openlocfilehash: b062efadca9ccfe2e2caeb054f662becc0807b50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530274"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Uso di XAML con app DirectX olografiche

> [!NOTE]
> Questo articolo si riferisce alle API native di WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare l' **[API OpenXR](../native/openxr-getting-started.md)**.

Questo argomento illustra l'effetto del cambio tra [visualizzazioni XAML 2D e viste immersive](../../design/app-views.md) nell'app DirectX e come usare in modo efficiente sia una visualizzazione XAML che una visualizzazione immersiva.

## <a name="xaml-view-switching-overview"></a>Panoramica sul cambio di visualizzazione XAML

In HoloLens un'app immersiva che può visualizzare in seguito una visualizzazione XAML 2D deve inizializzare prima la visualizzazione XAML e passare immediatamente a una visualizzazione immersiva. XAML verrà caricato prima che l'app possa eseguire qualsiasi operazione, che aggiunge un piccolo aumento al tempo di avvio. XAML continuerà a occupare lo spazio di memoria nel processo dell'app mentre rimane in background. La quantità di ritardo di avvio e di utilizzo della memoria dipende dalle operazioni svolte dall'app con XAML prima di passare alla visualizzazione nativa. Se non si esegue alcuna operazione nel codice di avvio XAML inizialmente, tranne che per iniziare la visualizzazione immersiva, l'effetto dovrebbe essere minore. Inoltre, poiché il rendering olografico viene eseguito direttamente nella visualizzazione immersiva, si eviteranno eventuali restrizioni correlate a XAML su tale rendering.

I conteggi di utilizzo della memoria per CPU e GPU. Direct3D 11 può scambiare memoria grafica virtuale, ma potrebbe non essere in grado di scambiare alcune o tutte le risorse GPU XAML e potrebbe essersi verificato un notevole impatto sulle prestazioni. In entrambi i casi, se non si caricano funzionalità XAML non necessarie, non sarà più disponibile una maggiore quantità di spazio per l'app e sarà possibile migliorare l'esperienza.

## <a name="xaml-view-switching-workflow"></a>Flusso di lavoro cambio visualizzazione XAML

Il flusso di lavoro per un'app che passa direttamente da XAML alla modalità immersiva è simile al seguente:
* L'app viene avviata nella visualizzazione XAML 2D.
* La sequenza di avvio XAML dell'app rileva se il sistema corrente supporta il rendering olografico:
* In tal caso, l'app crea la visualizzazione immersiva e la porta immediatamente in primo piano. Il caricamento XAML viene ignorato per tutto ciò che non è necessario nei dispositivi di realtà mista di Windows, incluse le classi di rendering e il caricamento di asset nella visualizzazione XAML. Se l'app usa XAML per l'input da tastiera, è comunque necessario creare la pagina di input.
* In caso contrario, la visualizzazione XAML può continuare con l'attività aziendale come di consueto.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Suggerimento per il rendering di elementi grafici in entrambe le visualizzazioni

Se l'app deve implementare una certa quantità di rendering in DirectX per la visualizzazione XAML in realtà mista di Windows, la scommessa migliore consiste nel creare un renderer che può funzionare con entrambe le visualizzazioni. Il renderer deve essere un'istanza a cui è possibile accedere da entrambe le visualizzazioni e deve passare dal rendering 2D a quello olografico. In questo modo, gli asset GPU vengono caricati solo una volta, riducendo i tempi di caricamento, l'effetto della memoria e la quantità di risorse scambiate durante il passaggio delle visualizzazioni.
