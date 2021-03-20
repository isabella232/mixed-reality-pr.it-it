---
title: README_Tooltip
description: Panoramica della descrizione comando in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, descrizione comando,
ms.openlocfilehash: 1177a6456ac2cb63976de14c9d49c322a810d647
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694808"
---
# <a name="tooltip"></a>Descrizione comando

![Descrizione comando principale](Images/Tooltip/MRTK_Tooltip_Main.png)

Le descrizioni comandi vengono in genere utilizzate per fornire un suggerimento o informazioni aggiuntive su un controllo più approfondito di un oggetto. È possibile utilizzare le descrizioni comandi per aggiungere annotazioni agli oggetti nell'ambiente fisico.

## <a name="how-to-use-a-tooltip"></a>Come usare una descrizione comando

Una descrizione comando può essere aggiunta direttamente alla gerarchia e destinata a un oggetto.

Per usare questo metodo, è sufficiente aggiungere un oggetto Game e una delle precompilate ToolTip (assets/MRTK/SDK/features/UX/prefabrics/Tooltips) alla gerarchia di scene. Nel pannello di controllo del prefabbricato espandere lo [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) script. Selezionare uno stato tip e configurare la descrizione comando.  Immettere il testo corrispondente per la descrizione comando nel campo di testo. Espandere lo [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) script e trascinare l'oggetto che deve avere la descrizione comando dalla gerarchia nel campo *destinazione* con etichetta. In questo modo la descrizione comando viene associata all'oggetto.
![Connettore descrizione comando](Images/Tooltip/MRTK_Tooltip_Connector.png)

Questo utilizzo presuppone una descrizione comando che viene sempre visualizzata o mostrata/nascosta tramite script modificando la proprietà dello stato della descrizione comando del componente ToolTip.

## <a name="dynamically-spawning-tooltips"></a>Generazione dinamica di descrizioni comandi

Una descrizione comando può essere aggiunta dinamicamente a un oggetto in fase di esecuzione, nonché preimpostata per visualizzare e nascondere un tocco o uno stato attivo. È sufficiente aggiungere lo [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) script a un oggetto Game. I ritardi per la visualizzazione e la scomparsa possono essere impostati nel controllo degli script, oltre che in una durata, in modo che la descrizione comando scomparirà dopo una durata impostata. Le descrizioni comandi includono anche le proprietà di stile, ad esempio gli oggetti visivi in background nello script del generatore. Per impostazione predefinita, la descrizione comando verrà ancorata all'oggetto con lo script di generazione. Questa operazione può essere modificata assegnando un GameObject al campo di ancoraggio.

## <a name="example-scene"></a>Scena di esempio

Nelle scene di esempio (assets/MRTK/examples/Demos/UX/Tooltips/scenes), sarà possibile trovare diversi esempi di descrizioni comandi.

![Esempi di descrizione comando](Images/Tooltip/MRTK_Tooltip_Examples.png)
