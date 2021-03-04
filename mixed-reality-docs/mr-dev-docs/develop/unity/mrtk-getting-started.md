---
title: Introduzione a MRKT per Unity
description: Introduzione a tutte le funzionalità che Mixed Reality Toolkit con supporto multipiattaforma può offrire ai nuovi sviluppatori di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, multipiattaforma
ms.openlocfilehash: b2fdf1114e30afc3d34582ebb71dd24bb8bf324d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759707"
---
# <a name="introducing-mrtk-for-unity"></a>Introduzione a MRKT per Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Che cos'è Mixed Reality Toolkit (MRTK)?

MRTK è uno straordinario toolkit open source disponibile sin dalla prima versione di HoloLens. Il toolkit non avrebbe raggiunto i livelli attuali senza il contributo e l'impegno costante della community di sviluppatori Microsoft. Negli ultimi tre anni abbiamo acquisito feedback dalla community di sviluppatori e abbiamo creato MRTK v2 tenendo conto delle principali esigenze e segnalazioni.  

MRTK per Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. Il modo più semplice per installare il Toolkit è con la nuova applicazione di strumenti per la funzionalità di realtà mista. Seguire le [istruzioni per l'installazione e l'utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto **mixed reality Toolkit Foundation** nella categoria Mixed Reality Toolkit. 

MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

Per altri dettagli sulle funzionalità, vedere la [documentazione di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/) .

## <a name="new-with-mrtk-v2"></a>Novità di MRTK v2

È importante sottolineare l'impegno che abbiamo dedicato a questi strumenti della piattaforma.  Infatti, abbiamo usato MRTK versione 2 per sviluppare le esperienze integrate, come l'esperienza di installazione predefinita (OOBE) e l'applicazione Mixed Reality Tips. Probabilmente avrai l'occasione anche di vedere nuove funzionalità di HoloLens 2 esposte tramite MRTK prima del rilascio, perché crediamo che questo sia il modo migliore per sviluppare sulla nostra piattaforma. 

### <a name="modular"></a>Modularità

Il toolkit è stato creato in modo modulare, quindi non è necessario includerlo per intero nel progetto.  Questa caratteristica presenta alcuni vantaggi.  Consente di limitare le dimensioni del progetto e ne semplifica la gestione.  Inoltre, poiché il toolkit è stato creato con oggetti gestibili tramite script ed è dotato di interfaccia, puoi anche sostituire i componenti inclusi nel toolkit con componenti personalizzati, per supportare altri servizi, sistemi e piattaforme.

### <a name="cross-platform"></a>Multipiattaforma

Il toolkit include il supporto per più piattaforme.  Anche se questo non significa che ogni singola piattaforma sia supportata, Microsoft ha fatto in modo che nessuna parte di codice del toolkit smetta di funzionare quando si scelgono altre piattaforme di destinazione per la build.  L'affidabilità e l'estendibilità della progettazione modulare permettono alle app di supportare più piattaforme, ad esempio ARCore, ARKit e OpenVR.

### <a name="performant"></a>Ottime prestazioni

Dovendo lavorare con piattaforme mobili, abbiamo realizzato il toolkit tenendo sempre ben presenti le prestazioni.  Questo aspetto è molto importante e Microsoft ha voluto assicurarsi che gli strumenti non creino difficoltà agli utenti.

## <a name="see-also"></a>Vedere anche

* [Installare gli strumenti](../install-the-tools.md)
* [Strumento per la funzionalità di realtà mista](welcome-to-mr-feature-tool.md)
* [Sviluppo con MRTK per Unity](unity-development-overview.md)
* [MRTK-Home page della documentazione](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/)
* [Porting da HoloToolkit/MRTK a MRTK versione 2 (GitHub)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/updates-deployment/hrtk-to-mrtk-porting-guide.md)
