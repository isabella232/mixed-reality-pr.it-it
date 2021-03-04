---
title: BoundarySystemGettingStarted
description: Pagina di destinazione per il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 7c3e9e7a65a636bbd2efac651f42608f13a0a562
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782038"
---
# <a name="boundary-system"></a>Sistema di limiti

Il sistema di limiti fornisce il supporto per la visualizzazione dei componenti limite della realtà virtuale nelle applicazioni di realtà mista. I limiti definiscono l'area in cui gli utenti possono spostarsi in modo sicuro mentre indossano una cuffia virtuale. I limiti sono un componente importante di un'esperienza di realtà mista per aiutare gli utenti a evitare gli ostacoli non visibili mentre indossano una cuffia virtuale.

Molte piattaforme di realtà virtuale forniscono una visualizzazione automatica, ad esempio un contorno bianco sovrapposto al mondo virtuale quando l'utente o il controller si avvicina al limite. Il sistema di limiti del Toolkit di realtà mista estende questa funzionalità per consentire la visualizzazione di una struttura dell'area rilevata, un piano di piano e altre funzionalità che possono essere usate per fornire informazioni aggiuntive agli utenti.

## <a name="getting-started"></a>Guida introduttiva

L'aggiunta del supporto per i limiti richiede due componenti chiave del Toolkit di realtà mista: il sistema di limiti e una piattaforma di realtà virtuale configurata con un limite.

1. [Abilitare](#enable-boundary-system) il sistema di limiti
2. [Configurare](#configure-boundary-visualization) la visualizzazione dei limiti
3. [Compila e Distribuisci](#build-and-deploy) in una piattaforma VR con un limite configurato

## <a name="enable-boundary-system"></a>Abilita sistema limite

Il sistema di limiti è gestito dall'oggetto MixedRealityToolkit (o da un altro componente di [registrazione del servizio](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).

I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar di servizi potrebbero essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../Images/MRTK_ConfiguredHierarchy.png)

1. Passare al pannello di controllo nella sezione del sistema di limiti e selezionare Abilita.

    ![Abilitare il sistema di limiti](../Images/Boundary/MRTKConfig_Boundary.png)

1. Selezionare l'implementazione del sistema di limiti. L'implementazione della classe predefinita fornita da MRTK è [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![Selezionare l'implementazione del sistema di limiti](../Images/Boundary/BoundarySelectSystemType.png)

> [!NOTE]
> Tutte le implementazioni del sistema limite devono estendere [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>Configurare la visualizzazione limite

Il [sistema di limiti USA un profilo di configurazione](ConfiguringBoundaryVisualization.md) per specificare quali componenti limite devono essere visualizzati e per configurarne l'aspetto.

![Opzioni di visualizzazione limite](../Images/Boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> Gli utenti del profilo predefinito, `DefaultMixedRealityBoundaryVisualizationProfile` (assets/MRTK/SDK/Profiles) avranno il sistema di limiti preconfigurato per visualizzare un piano di piano, l'area di riproduzione e l'area rilevata.

## <a name="build-and-deploy"></a>Eseguire la compilazione e la distribuzione

Una volta configurato il sistema di limiti con le opzioni di visualizzazione desiderate, è possibile compilare il progetto distribuito nella piattaforma di destinazione.

> [!NOTE]
> La modalità di riproduzione Unity consente la visualizzazione all'interno dell'editor del limite configurato. Questa funzionalità consente lo sviluppo e i test rapidi senza richiedere la fase di compilazione e distribuzione. Assicurarsi di eseguire test di accettazione finali usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.

## <a name="accessing-boundary-system-via-code"></a>Accesso al sistema di limiti tramite codice

Se abilitata e configurata, è possibile accedere al sistema di limiti tramite la classe helper statica CoreServices. Il riferimento può quindi essere usato per modificare dinamicamente i parametri limite e accedere a GameObject correlati gestiti dal sistema.

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API limite](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Configurazione della visualizzazione dei limiti](ConfiguringBoundaryVisualization.md)
