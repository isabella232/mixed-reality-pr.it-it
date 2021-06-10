---
title: Panoramica della conversione
description: Panoramica delle varie opzioni di porting per portare le applicazioni esistenti in Realtà mista per HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, motore, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600500"
---
# <a name="porting-overview"></a>Panoramica della conversione

Quando si tratta di eseguire il porting o l'aggiornamento dei progetti esistenti per la realtà mista, il percorso di porting dipende dal fatto che l'app sia compilata con Unity o Unreal Engine e che sia destinata a HoloLens (prima generazione) o HoloLens 2 o a SteamVR. Questa pagina di panoramica contiene le raccomandazioni correnti per ogni piattaforma e dispositivo. Assicurarsi di controllare di nuovo perché questi processi cambiano sempre.

Prima di tutto, configurare la destinazione del progetto in base alle raccomandazioni [di Unity](#unity) e [Unreal,](#unreal) quindi seguire uno o più scenari di porting:

- [HoloLens (prima generazione) per HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Visori VR di Windows Mixed Reality](#windows-mixed-reality-headsets)
- [App di SteamVR](#steamvr-applications)
- [App UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinazioni del progetto consigliate

È importante mantenere aggiornati i progetti, indipendentemente dal fatto che si trasla un'app in un altro dispositivo di destinazione. Per le raccomandazioni correnti, vedere le risorse basate sul motore elencate di seguito.

### <a name="unity"></a>Unity

La raccomandazione corrente per lo sviluppo di Unity con Realtà mista **è Unity 2019 LTS usando il pacchetto XR legacy.** Se il progetto usa Mixed Reality Toolkit, verificare di avere la versione più recente, attualmente **MRTK-Unity 2.5.**

> [!CAUTION]
> Anche se XR SDK è disponibile con questa versione di Unity, Ancoraggi nello spazio di Azure non è attualmente compatibile con questa configurazione. Questa raccomandazione verrà aggiornata con una versione futura del pacchetto Ancoraggi nello stato di Azure per Unity.
> 
> * Se non sono necessari ancoraggi nello stato di Azure, è possibile configurare il progetto Unity per [XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) e iniziare a usare [MRTK e XR SDK.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)
> 
> * Se si usa XR SDK nel progetto e si vuole usare Ancoraggi nello spaziali di Azure, disinstallare XR SDK e reinstallare il pacchetto XR legacy per ripristinare le impostazioni del progetto.

### <a name="unreal"></a>Unreal

La raccomandazione corrente per lo sviluppo unreal con realtà mista **è Unreal Engine 4.26.** Se il progetto usa Mixed Reality Toolkit UX Tools, assicurarsi di usare la versione più recente, attualmente **UXT 0.10.**

## <a name="porting-scenarios"></a>Scenari di porting

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>App Unity holoLens (prima generazione) da HoloLens 2

Se si dispone di un'applicazione Unity HoloLens (prima generazione) che si desidera convertire in un HoloLens 2, seguire le istruzioni nell'articolo sulla portabilità di [HoloLens.](./porting-hl1-hl2.md)

### <a name="windows-mixed-reality-headsets"></a>Visori VR di Windows Mixed Reality

Se hai creato contenuto per altri dispositivi, ad esempio Oculus Rift o HP Reverb G2, dovrai ridestinare gli SDK VR specifici del fornitore e potenzialmente le API di mapping dell'input. Le informazioni per gli scenari di porting Unity e Unreal sono disponibili nella guida alla porting delle [app immersive.](porting-guides.md)

### <a name="steamvr-applications"></a>Applicazioni di SteamVR

Per tutte le esperienze di SteamVR che si vuole aggiornare per Windows Mixed Reality visori, vedere la guida all'aggiornamento di [SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="2d-universal-windows-applications"></a>Applicazioni 2D universali di Windows

Se si ha un'app UWP 2D esistente che si desidera convertire in un visore vr immersivo Windows Mixed Reality o HoloLens, seguire le istruzioni per il porting delle app [UWP 2D](building-2d-apps.md) per Windows Mixed Reality video.