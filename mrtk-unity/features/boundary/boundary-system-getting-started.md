---
title: Panoramica del sistema di limiti
description: Pagina di destinazione per il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 134c92d8b3019ea8114f5bf50b7c4e3a19b0061f59a8266f6218a25f73c76449
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194417"
---
# <a name="boundary-system-overview"></a>Panoramica del sistema di limiti

Il sistema Boundary fornisce il supporto per la visualizzazione dei componenti limite di realtà virtuale nelle applicazioni di realtà mista. I limiti definiscono l'area in cui gli utenti possono spostarsi in modo sicuro mentre indossano un visore VR. I limiti sono un componente importante di un'esperienza di realtà mista per aiutare gli utenti a evitare ostacoli nonvisibile mentre indossano un visore VR.

Molte piattaforme di realtà virtuale offrono una visualizzazione automatica, ad esempio un contorno bianco sovrapposto al mondo virtuale quando l'utente o il relativo controller si avvicina al limite. Il sistema di limiti di Mixed Reality Toolkit estende questa funzionalità per consentire la visualizzazione di un contorno dell'area tracciata, di un piano terra e di altre funzionalità che possono essere usate per fornire informazioni aggiuntive agli utenti.

## <a name="getting-started"></a>Guida introduttiva

L'aggiunta del supporto per i limiti richiede due componenti chiave del Toolkit di realtà mista: il sistema di limiti e una piattaforma di realtà virtuale configurata con un limite.

1. [Abilitare](#enable-boundary-system) il sistema di limiti
2. [Configurare la](#configure-boundary-visualization) visualizzazione dei limiti
3. [Compilare e distribuire](#build-and-deploy) in una piattaforma VR con un limite configurato

## <a name="enable-boundary-system"></a>Abilitare il sistema di limiti

Il sistema di limiti è gestito dall'oggetto MixedRealityToolkit (o da un altro [componente del registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) del servizio).

La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar del servizio possono essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Passare al pannello Inspector (Controllo) nella sezione Boundary System (Sistema limite) e selezionare Enable (Abilita)

    ![Abilitare il sistema di limiti](../images/boundary/MRTKConfig_Boundary.png)

1. Selezionare l'implementazione del sistema di limiti. L'implementazione predefinita della classe fornita da MRTK è l'oggetto [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![Selezionare l'implementazione del sistema di limiti](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> Tutte le implementazioni del sistema di limiti devono estendere [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>Configurare la visualizzazione dei limiti

Il [sistema di limiti usa un profilo di configurazione](configuring-boundary-visualization.md) per specificare i componenti limite da visualizzare e per configurarne l'aspetto.

![Opzioni di visualizzazione dei limiti](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> Gli utenti del profilo predefinito (Assets/MRTK/SDK/Profiles) avranno il sistema di limiti preconfigurato per visualizzare un piano terra, l'area di gioco e `DefaultMixedRealityBoundaryVisualizationProfile` l'area tracciata.

## <a name="build-and-deploy"></a>Eseguire la compilazione e la distribuzione

Dopo aver configurato il sistema di limiti con le opzioni di visualizzazione desiderate, il progetto può essere compilato distribuito nella piattaforma di destinazione.

> [!NOTE]
> La modalità di riproduzione Unity abilita la visualizzazione nell'editor del limite configurato. Questa funzionalità consente di sviluppare e testare rapidamente senza richiedere il passaggio di compilazione e distribuzione. Assicurarsi di eseguire il test di accettazione finale usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.

## <a name="accessing-boundary-system-via-code"></a>Accesso al sistema di limiti tramite codice

Se abilitata e configurata, è possibile accedere al sistema di limiti tramite la classe helper statica CoreServices. Il riferimento può quindi essere usato per modificare dinamicamente i parametri Boundary e accedere agli oggetti GameObject correlati gestiti dal sistema.

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API Boundary](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Configurazione della visualizzazione dei limiti](configuring-boundary-visualization.md)
