---
title: InputFeatureUsageTool
description: Strumento InputFeatureUsage della documentazione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 35b28557df37abee19a0c950b362117eb6a120b0
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300201"
---
# <a name="inputfeatureusage-tool"></a>Strumento InputFeatureUsage

Lo strumento InputFeatureUsage è uno strumento di runtime (su dispositivo o Editor) che consente agli sviluppatori di determinare rapidamente i InputFeatureUsages Unity disponibili per un'origine di input rilevata (ad esempio, Motion controller o mano articolata).

> [!NOTE]
> Questa scena funziona solo in Unity 2019,3 o versioni successive.

Questo strumento è molto utile per lo sviluppo del supporto per un nuovo controller hardware. Può anche essere utile per confermare un problema di mapping del controllo sospetto nella classe di supporto per un controller esistente.

![Strumento InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Uso dello strumento InputFeatureUsage

Per iniziare a usare lo strumento InputFeatureUsage, passare a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** e aprire la scena **InputFeatureUsageTool** . Una volta caricata la scena, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione, oppure compilato ed eseguito in un dispositivo.

Per esaminare i mapping di Unity per un controller:

- Connettere il controller
- Premere ciascun pulsante e spostare ogni asse
- Si notino gli utilizzi delle funzionalità nella visualizzazione
- Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller

> [!NOTE]
> Lo strumento InputFeatureUsage non usa i componenti di Microsoft Mixed Reality Toolkit. Comunica direttamente con Unity per determinare e visualizzare gli utilizzi delle funzionalità.

### <a name="panels"></a>Pannelli

I pannelli visualizzano lo stato corrente di tutti i InputFeatureUsages segnalati in tutte le origini di input Unity rilevate.

Il pannello più piccolo lungo la parte superiore elenca i nomi di tutte le origini rilevate.

## <a name="see-also"></a>Vedere anche

- [Creazione di un provider di dati di sistema di input](../input/create-data-provider.md)
- [Strumento di mapping controller](controller-mapping-tool.md)
