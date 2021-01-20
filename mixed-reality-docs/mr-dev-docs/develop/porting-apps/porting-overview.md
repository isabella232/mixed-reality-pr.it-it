---
title: Panoramica della conversione
description: Panoramica delle varie opzioni di porting per l'uso delle applicazioni esistenti per la realtà mista per HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, Unity, middleware, motore, UWP, Win32
ms.openlocfilehash: 268d98b45aa659614e0266bfd1add7c7ed2f684a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583579"
---
# <a name="porting-overview"></a>Panoramica della conversione

Quando si tratta di eseguire il porting o l'aggiornamento dei progetti esistenti per la realtà mista, il percorso di porting dipende dal fatto che l'app venga compilata con Unity o Unreal Engine e abbia come destinazione HoloLens (1st Gen) o HoloLens 2 o SteamVR. Questa pagina di panoramica contiene le raccomandazioni correnti per ogni piattaforma e dispositivo. Assicurarsi di controllare quando questi processi cambiano sempre.

Per prima cosa, configurare la destinazione del progetto in base a [Unity](#unity) e ai consigli non [reali](#unreal) , quindi seguire uno o più dei nostri scenari di porting:

- [HoloLens (1a generazione) a HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Visori VR di Windows Mixed Reality](#windows-mixed-reality-headsets)
- [App SteamVR](#steamvr-applications)
- [app UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinazioni progetto consigliate

È importante lasciare aggiornati i progetti, sia che si tratti di trasferire un'app a un altro dispositivo di destinazione. Per le raccomandazioni correnti, fare riferimento alle risorse basate su motore elencate di seguito.

### <a name="unity"></a>Unity

L'attuale Consiglio per lo sviluppo di Unity con realtà mista è **unity 2019 LTS che usa il pacchetto XR legacy**. Se il progetto usa il Toolkit per la realtà mista, verificare che sia disponibile la versione più recente, che attualmente è **MRTK-unity 2,5**.

> [!CAUTION]
> Sebbene l'SDK di XR sia disponibile con questa versione di Unity, gli ancoraggi spaziali di Azure non sono attualmente compatibili con questa configurazione. Questa raccomandazione verrà aggiornata con una versione futura del pacchetto di ancoraggi spaziali di Azure per Unity. 
> 
> * Se non sono necessari ancoraggi spaziali di Azure, è possibile [configurare il progetto Unity per XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) e iniziare [a usare MRTK e XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).
> 
> * Se attualmente si usa l'SDK XR nel progetto e si vogliono usare gli ancoraggi spaziali di Azure, disinstallare XR SDK e reinstallare il pacchetto XR legacy per ripristinare le impostazioni del progetto.


### <a name="unreal"></a>Unreal 

Il nostro Consiglio attuale per lo sviluppo non reale con realtà mista è **Unreal Engine 4,26**. Se il progetto usa gli strumenti UX reality Toolkit, assicurarsi di usare la versione più recente, attualmente **UXT 0,10**.

## <a name="porting-scenarios"></a>Scenari di porting

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (1st Gen) Unity Apps to HoloLens 2

Se si dispone di un'applicazione HoloLens (1st Gen) Unity esistente che si desidera trasferire a un HoloLens 2, seguire le istruzioni contenute nell'articolo relativo al [porting di HoloLens](./porting-hl1-hl2.md).

### <a name="windows-mixed-reality-headsets"></a>Visori VR di Windows Mixed Reality

Se è stato compilato contenuto per altri dispositivi, ad esempio Oculus Rift o HP Reverb G2, sarà necessario ridestinare gli SDK VR specifici del fornitore e le API di mapping di input. È possibile trovare informazioni per gli scenari Unity e Unreal porting nella [Guida alla portabilità delle app immersive](porting-guides.md).

### <a name="steamvr-applications"></a>Applicazioni SteamVR

Per qualsiasi esperienza SteamVR che si vuole aggiornare per gli auricolari di realtà mista di Windows, vedere la [Guida all'aggiornamento di SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>applicazioni Windows universali 2D

Se si dispone di un'app UWP 2D esistente che si desidera trasferire a un auricolare o a un HoloLens per la realtà mista di Windows, seguire le istruzioni [per il porting di UWP 2D per la realtà mista di Windows](building-2d-apps.md) .