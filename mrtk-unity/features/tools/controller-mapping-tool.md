---
title: Strumento di mapping dei controller
description: Documentazione sullo strumento di mapping dei controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f00dc01555ef158dab21334761bd23ef6a70dba4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144083"
---
# <a name="controller-mapping-tool"></a>Strumento di mapping dei controller

Lo strumento di mapping dei controller è uno strumento di runtime (nel dispositivo o nell'editor) che consente agli sviluppatori di determinare rapidamente l'asse di input di Unity e i mapping dei pulsanti per un controller hardware (ad esempio, controller di movimento).

Questo strumento è molto utile quando si sviluppa il supporto per un nuovo controller hardware. Può anche essere utile per confermare un sospetto problema di mapping dei controlli nella classe di supporto per un controller esistente.

![Strumento di mapping dei controller](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Uso dello strumento di mapping dei controller

Per iniziare a usare lo strumento di mapping dei controller, passare a **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** e aprire la **scena ControllerMappingTool.** Dopo aver caricato la scena, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione o compilato ed eseguito in un dispositivo.

Per esaminare i mapping di Unity per un controller:

- Connettere il controller
- Premere ogni pulsante e spostare ogni asse
- Prendere nota dei mapping nella visualizzazione
- Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller

> [!NOTE]
> Lo strumento di mapping dei controller non usa i componenti di Microsoft Mixed Reality Toolkit. Comunica direttamente con Unity per determinare e visualizzare i mapping dei controlli.

### <a name="all-controls-display"></a>Visualizzazione di tutti i controlli

Il pannello di visualizzazione di grandi dimensioni segnala lo stato di tutti gli assi e i pulsanti di input di Unity definiti (ad esempio: Asse 10, Pulsante 3). Questo pannello offre una visualizzazione completa dello stato del controller.

![Visualizzazione di tutti i controlli](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Visualizzazione dei controlli attivi

Il pannello di visualizzazione più piccolo e ristretto mostra l'asse di input di Unity e i pulsanti che si trova in uno stato attivo (ad esempio, viene premuto un pulsante). La visualizzazione dei controlli attivi offre una visualizzazione di riepilogo facile da leggere dello stato del controller.

![Visualizzazione dei controlli attivi](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Vedi anche

- [Creazione di un provider di dati del sistema di input](../input/create-data-provider.md)
- [Strumento InputFeatureUsage](input-feature-usage-tool.md)
