---
title: Introduzione a MRTK per Unreal
description: Introduzione a tutto ciò che Mixed Reality Toolkit per Unreal offre nuovi sviluppatori di realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, multipiattaforma
ms.openlocfilehash: 3d46b92dbf3182ca5a50a8e106d2b947e4f7120f
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394285"
---
# <a name="introducing-mrtk-for-unreal"></a>Introduzione a MRTK per Unreal

![Immagine del banner MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Che cos'è Mixed Reality Toolkit (MRTK)?

MRTK è uno straordinario toolkit open source disponibile sin dalla prima versione di HoloLens. Il toolkit non avrebbe raggiunto i livelli attuali senza il contributo e l'impegno costante della community di sviluppatori Microsoft. 

Mixed Reality Toolkit for Unreal (MRTK-Unreal) è un set di componenti, sotto forma di plug-in, esempi e documentazione, progettati per facilitare lo sviluppo di applicazioni di realtà mista usando il motore Unreal. Attualmente, il toolkit è costituito da:
* [UX Tools for Unreal,](https://github.com/microsoft/MixedReality-UXTools-Unreal)che fornisce codice, progetti ed esempi per implementare le funzionalità dell'esperienza utente per le applicazioni Hololens 2.
* [Strumenti di grafica per Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), che consente di migliorare la fedeltà visiva delle applicazioni di realtà mista mantenendo i budget per le prestazioni.

Esaminare la documentazione [di MRTK](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) in GitHub e iniziare a usare le guide all'installazione degli strumenti [UX](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) o [degli strumenti](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) di grafica.

### <a name="modular"></a>Modularità

È stato creato MRTK Unreal in modo modulare, quindi non è necessario importare tutti i componenti del toolkit nel progetto. È possibile selezionare e scegliere i plug-in necessari e aggiungerli o rimuoverli ogni volta che lo si desidera. Questo approccio mantiene le dimensioni del progetto più piccole e semplifica la gestione.  

### <a name="performant"></a>Ottime prestazioni

Lavorando con le piattaforme mobili, è stato creato MRTK Unreal con le prestazioni in considerazione. Si tratta di un aspetto estremamente importante e si è voluto garantire che gli strumenti non funzionino con l'utente.

## <a name="project-setup"></a>Configurazione del progetto

> [!div class="nextstepaction"]
> [Scaricare un motore Unreal e MRTK](unreal-project-setup.md)

## <a name="see-also"></a>Vedere anche

* [Installare gli strumenti](../install-the-tools.md)
* [Sviluppo con MRTK per Unreal](unreal-development-overview.md)
* [Strumenti dell'esperienza utente - Guida all'installazione (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [Strumenti dell'esperienza utente- Home page della documentazione (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [Strumenti di grafica - Guida all'installazione (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [Strumenti di grafica - Home page della documentazione (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)