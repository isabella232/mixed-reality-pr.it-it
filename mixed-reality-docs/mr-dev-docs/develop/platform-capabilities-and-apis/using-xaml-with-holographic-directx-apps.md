---
title: Uso di XAML con app DirectX olografiche
description: Illustra l'impatto del passaggio tra visualizzazioni XAML 2D e visualizzazioni immersive nell'app DirectX e come usare in modo efficiente sia una visualizzazione XAML che una visualizzazione immersiva.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows mixed reality, UWP, gestione della visualizzazione app, xaml, tastiera, procedura dettagliata, DirectX
ms.openlocfilehash: 3c7edfdf4ff2ed629699dca0514efabc9ce7241cb1781e4b9c914ad4bff1f900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220947"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Uso di XAML con app DirectX olografiche

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](../native/openxr-getting-started.md)**.

Questo argomento illustra l'impatto del passaggio tra visualizzazioni [XAML 2D](../../design/app-views.md) e visualizzazioni immersive nell'app DirectX e come usare in modo efficiente sia una visualizzazione XAML che una visualizzazione immersiva.

## <a name="xaml-view-switching-overview"></a>Panoramica del cambio di visualizzazione XAML

In HoloLens, un'app immersiva che in un secondo momento potrebbe visualizzare una visualizzazione XAML 2D deve prima inizializzare la visualizzazione XAML e passare immediatamente a una visualizzazione immersiva da qui. XAML verrà caricato prima che l'app possa eseguire qualsiasi operazione, con un piccolo aumento del tempo di avvio. XAML continuerà a occupare spazio di memoria nel processo dell'app mentre rimane in background. La quantità di ritardo di avvio e l'utilizzo della memoria dipendono dalle attività dell'app con XAML prima di passare alla visualizzazione nativa. Se all'inizio non si fa nulla nel codice di avvio XAML tranne avviare la visualizzazione immersiva, l'impatto dovrebbe essere minore. Inoltre, poiché il rendering olografico viene eseguito direttamente nella visualizzazione immersiva, si eviterà qualsiasi restrizione correlata a XAML per tale rendering.

Il conteggio dell'utilizzo della memoria per CPU e GPU. Direct3D 11 può scambiare memoria grafica virtuale, ma potrebbe non essere in grado di scambiare alcune o tutte le risorse DELLA GPU XAML e potrebbe verificarsi un notevole calo delle prestazioni. In entrambi i modi, il non caricamento di funzionalità XAML non necessarie lascia più spazio per l'app e offre un'esperienza migliore.

## <a name="xaml-view-switching-workflow"></a>Flusso di lavoro di cambio di visualizzazione XAML

Il flusso di lavoro per un'app che passa direttamente da XAML alla modalità immersive è simile al seguente:
* L'app viene avviata nella visualizzazione XAML 2D.
* La sequenza di avvio XAML dell'app rileva se il sistema corrente supporta il rendering olografico:
* In tal caso, l'app crea la visualizzazione immersiva e la porta immediatamente in primo piano. Il caricamento XAML viene ignorato per tutto ciò che non è necessario nei Windows Mixed Reality, incluse le classi di rendering e il caricamento di asset nella visualizzazione XAML. Se l'app usa XAML per l'input da tastiera, la pagina di input deve comunque essere creata.
* In caso contrario, la visualizzazione XAML può continuare a lavorare come di consueto.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Suggerimento per il rendering della grafica in entrambe le visualizzazioni

Se l'app deve implementare una certa quantità di rendering in DirectX per la visualizzazione XAML in Windows Mixed Reality, la soluzione migliore è creare un renderer in grado di funzionare con entrambe le visualizzazioni. Il renderer deve essere un'istanza accessibile da entrambe le visualizzazioni e deve passare dal rendering 2D al rendering olografico. In questo modo gli asset GPU vengono caricati una sola volta, riducendo i tempi di caricamento, l'impatto sulla memoria e la quantità di risorse scambiate quando si passa da una visualizzazione all'altra.
