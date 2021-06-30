---
title: Panoramica della conversione
description: Panoramica delle varie opzioni di porting per portare le applicazioni esistenti in Realtà mista per HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, motore, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042272"
---
# <a name="porting-overview"></a>Panoramica della conversione

Quando si tratta di eseguire il porting o l'aggiornamento dei progetti esistenti per la realtà mista, il percorso di porting dipende dal fatto che l'app sia compilata con Unity o Unreal Engine e che sia destinata a HoloLens (prima generazione) o HoloLens 2 o a SteamVR. Questa pagina di panoramica contiene le raccomandazioni correnti per ogni piattaforma e dispositivo. Assicurarsi di controllare di nuovo perché questi processi cambiano sempre.

Prima di tutto, configurare la destinazione del progetto in base alle raccomandazioni [di Unity](#unity) e [Unreal,](#unreal) quindi seguire uno o più scenari di porting:

- [HoloLens (prima generazione) per HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Visori VR immersive](#immersive-vr-headsets)
- [App UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinazioni del progetto consigliate

È importante mantenere aggiornati i progetti, indipendentemente dal fatto che si trasla un'app in un altro dispositivo di destinazione. Per le raccomandazioni correnti, vedere le risorse basate sul motore elencate di seguito.

### <a name="unity"></a>Unity

Per informazioni aggiornate sulle versioni [consigliate](../unity/choosing-unity-version.md) di Unity e MRTK, vedere la pagina Scelta di una versione di Unity.

### <a name="unreal"></a>Unreal

Per informazioni aggiornate sulle versioni consigliate di Unreal e MRTK, vedere la pagina Configurazione del progetto [Unreal.](../unreal/unreal-project-setup.md)

## <a name="porting-scenarios"></a>Scenari di porting

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>App Unity holoLens (prima generazione) da HoloLens 2

Se si dispone di un'applicazione Unity HoloLens (prima generazione) che si desidera convertire in un HoloLens 2, seguire le istruzioni nell'articolo sulla portabilità di [HoloLens.](./porting-hl1-hl2.md)

### <a name="immersive-vr-headsets"></a>Visori VR immersive

Se hai creato contenuto per altri dispositivi VR, dovrai ridestinare gli SDK VR specifici del fornitore e le API di mapping degli input potenzialmente. Le informazioni per gli scenari di porting Unity e Unreal sono disponibili nella guida alla porting delle [app immersive.](porting-guides.md)

Per le esperienze di SteamVR da aggiornare per Windows Mixed Reality visori, vedere la guida all'aggiornamento [di SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="2d-universal-windows-applications"></a>Applicazioni 2D universali di Windows

Se si ha un'app UWP 2D esistente che si desidera convertire in un visore vr immersivo Windows Mixed Reality o HoloLens, seguire le istruzioni per il porting delle app [UWP 2D](building-2d-apps.md) per Windows Mixed Reality video.