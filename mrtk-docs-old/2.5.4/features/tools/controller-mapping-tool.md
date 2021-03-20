---
title: ControllerMappingTool
description: Documentazione sullo strumento di mapping del controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: fb5f177a1de082c9904f0920b37702acd850a59e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104696218"
---
# <a name="controller-mapping-tool"></a>Strumento di mapping controller

Lo strumento di mapping del controller è un Runtime (su dispositivo o Editor) che consente agli sviluppatori di determinare rapidamente i mapping degli assi di input e dei pulsanti di Unity per un controller hardware (ad esempio, Motion controller).

Questo strumento è molto utile per lo sviluppo del supporto per un nuovo controller hardware. Può anche essere utile per confermare un problema di mapping del controllo sospetto nella classe di supporto per un controller esistente.

![Strumento di mapping controller](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Utilizzo dello strumento di mapping dei controller

Per iniziare a usare lo strumento di mapping del controller, passare a **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** e aprire la scena **ControllerMappingTool** . Una volta caricata la scena, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione, oppure compilato ed eseguito in un dispositivo.

Per esaminare i mapping di Unity per un controller:

- Connettere il controller
- Premere ciascun pulsante e spostare ogni asse
- Annotare i mapping nella visualizzazione
- Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller

> [!NOTE]
> Lo strumento di mapping del controller non usa i componenti di Microsoft Mixed Reality Toolkit. Comunica direttamente con Unity per determinare e visualizzare i mapping dei controlli.

### <a name="all-controls-display"></a>Visualizzazione di tutti i controlli

Il pannello di visualizzazione di grandi dimensioni segnala lo stato di tutti gli assi e i pulsanti di input Unity definiti, ad esempio asse 10, pulsante 3. Questo pannello offre una visualizzazione completa dello stato del controller.

![Visualizzazione di tutti i controlli](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Visualizzazione controlli attivi

Il pannello di visualizzazione più piccolo e ridotto Mostra i pulsanti e cartesiano di input Unity che si trovano in uno stato attivo (ad esempio, viene premuto un pulsante). La visualizzazione dei controlli attivi fornisce una visualizzazione riepilogativa di facile lettura dello stato del controller.

![Visualizzazione controlli attivi](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Vedi anche

- [Creazione di un provider di dati di sistema di input](../input/create-data-provider.md)
- [Strumento InputFeatureUsage](input-feature-usage-tool.md)
