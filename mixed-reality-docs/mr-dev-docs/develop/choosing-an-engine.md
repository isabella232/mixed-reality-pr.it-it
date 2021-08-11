---
title: Scelta del motore
description: Introduzione alle opzioni del motore disponibili per lo sviluppo di realtà mista per HoloLens realtà virtuale.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, unity
ms.openlocfilehash: 14235852f8c90e7ccc4f105f2938ce514ae2933973469db9a0e01bd03d2c1b6d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227553"
---
# <a name="choosing-your-engine"></a>Scelta del motore

Sono disponibili diversi percorsi di sviluppo che è possibile seguire attraverso la documentazione. Il primo passaggio consiste nell'individuare la tecnologia più adatta alle specifiche esigenze. Se se ne è già individuata una, è possibile passare direttamente alla rispettiva scheda riportata di seguito. Se ci si affaccia a questo ambiente per la prima volta o si è appena iniziato, è opportuno esaminare tutte le possibilità e comprendere cosa offrono, le piattaforme e gli strumenti disponibili e solo dopo iniziare a creare.

> [!IMPORTANT]
> Se si hanno a disposizione progetti da trasferire in HoloLens 2 o visori VR immersive come Reverb G2, consultare la **[panoramica delle guide per il porting](porting-apps/porting-overview.md)** . Sono disponibili guide per progetti che usano HTK, MRTK v1, SteamVR o che sono stati sviluppati per visori VR immersive, ad esempio Oculus Rift o HTC Vive.

## <a name="engine-overview"></a>Panoramica del motore

* **Unity** è una delle principali piattaforme di sviluppo in tempo reale sul mercato, con il codice di runtime sottostante scritto in C++ e tutto lo scripting di sviluppo viene eseguito in C#. Unity offre l'infrastruttura necessaria per supportare qualsiasi utente per la creazione di giochi, filmati e animazioni o anche per il rendering di concetti architettonici o ingegneristici in un mondo virtuale.

* **Unreal Engine 4 è** un motore di creazione di open source avanzato con supporto completo per la realtà mista sia in C++ che in Blueprints. A partire da Unreal Engine 4.25, il supporto per HoloLens è completo e pronto per la produzione. Grazie a funzionalità quali il sistema flessibile Blueprints Visual Scripting, i progettisti possono usare praticamente tutta la gamma di concetti e strumenti disponibili in genere solo per i programmatori. Autori di tutti i settori possono sfruttare la libertà e il controllo per offrire contenuti all'avanguardia, esperienze interattive e mondi virtuali immersivi.

* **Gli** sviluppatori nativi con esperienza nella scrittura di renderer 3D personalizzati possono creare un motore personalizzato usando OpenXR. OpenXR è uno standard API aperto, concesso a titolo gratuito da Khronos che fornisce ai motori l'accesso nativo a un'ampia gamma di dispositivi di fornitori che operano nell'ambito della realtà mista. È possibile sviluppare app usando OpenXR in un visore VR immersive di HoloLens 2 o Windows Mixed Reality sul desktop.

* **Gli sviluppatori Web** che creano esperienze Web AR/VR accattivanti tra browser possono usare **WebXR.**

    > [!NOTE]
    > **Babylon.js** per HoloLens lo sviluppo è attualmente in corso. Scopri le novità [più recenti e interagisci con la community.](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)

<!-- Babylon is a Javascript-based, open source, 3D graphics engine capable of powering 3D scenes in a web browser. Babylon.js 4.2+ includes support for WebXR. With Babylon React Native, you can even build cross-platform native     applications for PC, mobile, and mixed reality devices. -->

## <a name="features-and-devices"></a>Funzionalità e dispositivi

<br>

| Logistica | Unity | Unreal | JavaScript | Motore personalizzato <br>(con OpenXR) |
|---|---|---|---|---|
| Linguaggio | C# | C++ | JavaScript | C/C++ |
| Prezzi | [Prezzi di Unity](https://store.unity.com/#plans-individual) | [Prezzi di Unreal](https://www.unrealengine.com/download) | Gratuito | Gratuito |

<br>

| Funzionalità del dispositivo | Unity | Unreal | JavaScript | Motore personalizzato <br>(con OpenXR) |
|---|---|---|---|---|
| Rilevamento del dispositivo/dello schermo | ✔️ | ✔️ | ✔️ | ✔️ |
| Input manuale | ✔️ | ✔️ | ✔️ | ✔️ |
| Input oculare | ✔️ | ✔️ | ❌ | ✔️ |
| Input vocale | ✔️ | ✔️ | ✔️ | ✔️ |
| Controller del movimento | ✔️ | ✔️ | ✔️ | ✔️ |
| Hit testing piano/mesh | ✔️ | ✔️ | ✔️ | ✔️ |
| Informazioni sulle scene | ✔️ | ✔️ | ❌ | ✔️ |
| Audio spaziale | ✔️ | ✔️ | ✔️ | ✔️ |
| Rilevamento del codice a codici a qr | ✔️ | ✔️ | ❌ | ✔️ |

<br>

| Hardware | Unity | Unreal | JavaScript | Motore personalizzato <br>(con OpenXR) |
|---|---|---|---|---|
| HoloLens 2 | ✔️ | ✔️ | ✔️ | ✔️ |
| HoloLens (prima generazione) | ✔️ | ✔️ | ❌ | Solo WinRT (legacy) |
| [Visori VR di Windows Mixed Reality](../discover/immersive-headset-hardware-details.md) | ✔️ | ✔️ | ✔️ | ✔️ |
| Visori Per lavr a vapore | ✔️ | ✔️ | ✔️ | ✔️ |
| Oculus Quest/Rift | ✔️ | ✔️ | ✔️ | ✔️ |
| Mobile (ARCore/ARKit) | ✔️ | ✔️ | ✔️ | ❌ |

<br>

| Strumenti | Unity | Unreal | JavaScript | Motore personalizzato <br>(con OpenXR) |
|---|---|---|---|---|
| Mixed Reality Toolkit | ✔️ | ✔️ | ❌  | ❌ |
| Strumenti di blocco del mondo | ✔️ | ❌ | ❌  | ❌ |
<!-- | Mesh | ❌ | ❌ | ❌ | ❌ | -->

<br>

| Servizi cloud | Unity | Unreal | JavaScript | Motore personalizzato <br>(con OpenXR) |
|---|---|---|---|---|
| Ancoraggi nello spazio di Azure | ✔️ | ✔️ | ❌ | ✔️ |
| Ancoraggi di oggetti di Azure | ✔️ | ❌ | ❌ | ✔️ |
| Rendering remoto di Azure | ✔️ * | ❌ | ❌ | ✔️ * |

> [!NOTE]
> * Rendering remoto di Azure è attualmente supportato nelle app che usano le API WinRT legacy (Windows plug-in XR in Unity). Il supporto ARR per le app OpenXR sarà presto disponibile.

## <a name="next-steps"></a>Passaggi successivi

[!INCLUDE[](includes/tools-next-steps.md)]