---
title: Guida introduttiva a MRTK versione 2
description: Per i nuovi sviluppatori interessati a usufruire dei vantaggi offerti da MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: ed3663c9eb3735dc2232a667e605ba4dab5bf1a4
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573225"
---
# <a name="getting-started-with-mrtk-for-unity"></a>Introduzione a MRTK per Unity
![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Che cos'è Mixed Reality Toolkit (MRTK)?
MRTK è un toolkit open source eccezionale, disponibile da quando il dispositivo HoloLens è stato rilasciato per la prima volta, ma che oggi non sarebbe così efficace senza i preziosi contributi della nostra community di sviluppatori. Negli ultimi tre anni abbiamo acquisito feedback dalla nostra community di sviluppatori e abbiamo creato MRTK v2 tenendo conto delle loro principali esigenze e segnalazioni.  

MRTK per Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, di visori VR immersive di Windows Mixed Reality e della piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

Per altre informazioni, vedere la [documentazione di MRTK in GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html). Per iniziare, seguire la procedura descritta nella pagina relativa alla [guida all'installazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).


## <a name="new-with-mrtk-v2"></a>Novità di MRTK v2
È importante sottolineare l'impegno che abbiamo dedicato a questi strumenti della piattaforma.  Infatti, abbiamo usato MRTK versione 2 per sviluppare le esperienze integrate, come l'esperienza di installazione predefinita (OOBE) e l'applicazione Mixed Reality Tips. Probabilmente avrai l'occasione anche di vedere nuove funzionalità di HoloLens 2 esposte tramite MRTK prima del rilascio, perché crediamo che questo sia il modo migliore per sviluppare sulla nostra piattaforma. 

### <a name="modular"></a>Modularità
Il toolkit è stato creato in modo modulare, quindi non è necessario includerlo per intero nel progetto.  Questa caratteristica presenta alcuni vantaggi.  Consente di limitare le dimensioni del progetto e ne semplifica la gestione.  Inoltre, poiché il toolkit è stato creato con oggetti gestibili tramite script ed è dotato di interfaccia, puoi anche sostituire i componenti inclusi nel toolkit con componenti personalizzati, per supportare altri servizi, sistemi e piattaforme.

### <a name="cross-platform"></a>Multipiattaforma
Il toolkit include il supporto per più piattaforme.  Anche se questo non significa che ogni singola piattaforma è supportata in modo predefinito, abbiamo fatto in modo che nessuna parte del codice del toolkit smetta di funzionare nel caso in cui tu scelga di configurare altre piattaforme di destinazione per la tua build.  L'affidabilità e l'estendibilità che caratterizzano la progettazione modulare ti aiuteranno a seguire la strada giusta per supportare più piattaforme, come ARCore, ARKit e OpenVR.

### <a name="performant"></a>Ottime prestazioni
Dovendo lavorare con piattaforme mobili, abbiamo realizzato il toolkit tenendo sempre ben presenti le prestazioni.  Questo è un aspetto molto importante e volevamo essere sicuri che gli strumenti funzionassero nel modo giusto.

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](../install-the-tools.md)
* [MRTK - Guida all'installazione (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK - Home page della documentazione (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Porting da HoloToolkit/MRTK a MRTK versione 2 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
