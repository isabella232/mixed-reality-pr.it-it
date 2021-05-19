---
title: Strumento di utilizzo delle funzionalità di input
description: Strumento InputFeatureUsage della documentazione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145012"
---
# <a name="inputfeatureusage-tool"></a>Strumento InputFeatureUsage

Lo strumento InputFeatureUsage è uno strumento di runtime (nel dispositivo o nell'editor) che consente agli sviluppatori di determinare rapidamente l'input UnityFeatureUsages disponibile per un'origine di input rilevata (ad esempio controller di movimento o mano articolata).

> [!NOTE]
> Questa scena funziona solo in Unity 2019.3 o versione successiva.

Questo strumento è molto utile quando si sviluppa il supporto per un nuovo controller hardware. Può anche essere utile per confermare un sospetto problema di mapping dei controlli nella classe di supporto per un controller esistente.

![Strumento InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Uso dello strumento InputFeatureUsage

Per iniziare a usare lo strumento InputFeatureUsage, passare a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** e aprire la **scena InputFeatureUsageTool.** Dopo aver caricato la scena, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione o compilato ed eseguito in un dispositivo.

Per esaminare i mapping di Unity per un controller:

- Connettere il controller
- Premere ogni pulsante e spostare ogni asse
- Si notino gli utilizzi delle funzionalità nella visualizzazione
- Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller

> [!NOTE]
> Lo strumento InputFeatureUsage non usa i componenti di Microsoft Mixed Reality Toolkit. Comunica direttamente con Unity per determinare e visualizzare gli utilizzi delle funzionalità.

### <a name="panels"></a>Pannelli

I pannelli visualizzano lo stato corrente di tutte le inputFeatureUsages segnalate in tutte le origini di input unity rilevate.

Il pannello più piccolo nella parte superiore elenca i nomi di tutte le origini rilevate.

## <a name="see-also"></a>Vedi anche

- [Creazione di un provider di dati del sistema di input](../input/create-data-provider.md)
- [Strumento di mapping del controller](controller-mapping-tool.md)
