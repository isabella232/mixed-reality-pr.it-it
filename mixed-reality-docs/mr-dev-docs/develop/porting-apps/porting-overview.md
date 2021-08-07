---
title: Panoramica della conversione
description: Panoramica delle varie opzioni di porting per portare le applicazioni esistenti in realtà mista per HoloLens vr.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, motore, UWP, Win32
ms.openlocfilehash: 519dae088e689e0a6e617bf5e2b34f81cc2e265256c4844df7dd34e99172d536
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189421"
---
# <a name="porting-overview"></a>Panoramica della conversione

Quando si tratta di eseguire il porting o l'aggiornamento dei progetti esistenti per la realtà mista, il percorso di porting dipende dal fatto che l'app sia compilata con Unity o Unreal Engine e sia destinata a HoloLens (prima generazione) o HoloLens 2 o a SteamVR. Questa pagina di panoramica contiene le raccomandazioni correnti per ogni piattaforma e dispositivo. Assicurarsi di controllare di nuovo perché questi processi cambiano sempre.

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

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (prima generazione) di Unity da HoloLens 2

Se si dispone di un'applicazione Unity HoloLens (prima generazione) che si desidera convertire in un HoloLens 2, seguire le istruzioni nell'articolo HoloLens [porting](./porting-hl1-hl2.md).

### <a name="immersive-vr-headsets"></a>Visori VR immersive

Se hai creato contenuto per altri dispositivi VR, dovrai ridestinare gli SDK VR specifici del fornitore e le API di mapping degli input potenzialmente. Le informazioni per gli scenari di porting Unity e Unreal sono disponibili nella guida alla porting delle [app immersive.](porting-guides.md)

Per le esperienze di SteamVR da aggiornare per Windows Mixed Reality visori, vedere la guida all'aggiornamento [di SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="2d-universal-windows-applications"></a>Applicazioni universali Windows 2D

Se si ha un'app UWP 2D esistente che si desidera convertire Windows Mixed Reality visore immersive o HoloLens, seguire le istruzioni per il porting delle app [UWP 2D](building-2d-apps.md) Windows Mixed Reality.