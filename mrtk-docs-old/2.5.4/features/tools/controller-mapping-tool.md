---
title: Strumento ControllerMappingTool
description: Documentazione sullo strumento di mapping dei controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4a2ad67916d2fb9dd5fb3f4061934a27e3aa8763d64c5561a6e1b178a708069a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199797"
---
# <a name="controller-mapping-tool"></a>Strumento di mapping del controller

Lo strumento di mapping del controller è uno strumento di runtime (nel dispositivo o nell'editor) che consente agli sviluppatori di determinare rapidamente l'asse di input Unity e i mapping dei pulsanti per un controller hardware (ad esempio, un controller del movimento).

Questo strumento è molto utile quando si sviluppa il supporto per un nuovo controller hardware. Può anche essere utile per confermare un sospetto problema di mapping dei controlli nella classe di supporto per un controller esistente.

![Strumento di mapping del controller](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Uso dello strumento di mapping del controller

Per iniziare a usare lo strumento di mapping del controller, passare a **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** e aprire la **scena ControllerMappingTool.** Dopo che la scena è stata caricata, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione o compilato ed eseguito in un dispositivo.

Per esaminare i mapping di Unity per un controller:

- Connessione il controller
- Premere ogni pulsante e spostare ogni asse
- Si notino i mapping nella visualizzazione
- Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller

> [!NOTE]
> Lo strumento di mapping del controller non usa Microsoft Mixed Reality Toolkit componenti. Comunica direttamente con Unity per determinare e visualizzare i mapping dei controlli.

### <a name="all-controls-display"></a>Visualizzazione di tutti i controlli

Il pannello di visualizzazione di grandi dimensioni segnala lo stato di tutti gli assi e i pulsanti di input di Unity definiti (ad esempio: Asse 10, Pulsante 3). Questo pannello offre una visualizzazione completa dello stato del controller.

![Visualizzazione di tutti i controlli](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Visualizzazione dei controlli attivi

Il pannello di visualizzazione più piccolo e ristretto mostra l'asse di input di Unity e i pulsanti che si trova in uno stato attivo (ad esempio, viene premuto un pulsante). La visualizzazione dei controlli attivi offre una visualizzazione di riepilogo facile da leggere dello stato del controller.

![Visualizzazione dei controlli attivi](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Vedi anche

- [Creazione di un provider di dati del sistema di input](../input/create-data-provider.md)
- [Strumento InputFeatureUsage](input-feature-usage-tool.md)
