---
title: Descrizione comando
description: Panoramica della descrizione comando in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, descrizione comando,
ms.openlocfilehash: af848db0962948b1f2ada73066c4ae90730b09a99dea231ebf468a05441b85ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196323"
---
# <a name="tooltip"></a>Descrizione comando

![Descrizione comando principale](../images/tooltip/MRTK_Tooltip_Main.png)

Le descrizioni comando vengono in genere usate per comunicare un suggerimento o informazioni aggiuntive dopo un'analisi più vicina di un oggetto. Le descrizioni comando possono essere usate per annotare oggetti nell'ambiente fisico.

## <a name="how-to-use-a-tooltip"></a>Come usare una descrizione comando

Una descrizione comando può essere aggiunta direttamente alla gerarchia e destinata a un oggetto .

Per usare questo metodo, è sufficiente aggiungere un oggetto gioco e uno dei prefab di descrizione comando (Assets/MRTK/SDK/Features/UX/Prefabs/Tooltips) alla gerarchia della scena. Nel pannello di controllo del prefab espandere lo [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) script. Selezionare uno stato della mancia e configurare la descrizione comando.  Immettere il testo corrispondente per la descrizione comando nel campo di testo. Espandere lo [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) script e trascinare l'oggetto che deve avere la descrizione comando dalla gerarchia nel campo con etichetta *Target*. In questo modo la descrizione comando viene collegata all'oggetto .
![Connettore descrizione comando](../images/tooltip/MRTK_Tooltip_Connector.png)

Questo uso presuppone una descrizione comando che viene sempre visualizzata o che viene visualizzata/nascosta tramite script modificando la proprietà dello stato della descrizione comando del componente della descrizione comando.

## <a name="dynamically-spawning-tooltips"></a>Generazione dinamica di descrizioni comando

Una descrizione comando può essere aggiunta dinamicamente a un oggetto in fase di esecuzione, nonché pre-impostata per mostrare e nascondere un tocco o lo stato attivo. È sufficiente aggiungere lo [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) script a qualsiasi oggetto gioco. I ritardi per la visualizzazione e la scomparsa possono essere impostati nel controllo script, nonché una durata in modo che la descrizione comando scompaia dopo una durata impostata. Le descrizioni comando presentano anche proprietà di stile, ad esempio gli oggetti visivi di sfondo nello script dello strumento di generazione. Per impostazione predefinita, la descrizione comando verrà ancorata all'oggetto con lo script dello strumento di generazione. Questo può essere modificato assegnando un GameObject al campo di ancoraggio.

## <a name="example-scene"></a>Scena di esempio

Nelle scene di esempio (Assets/MRTK/Examples/Demos/UX/Tooltips/Scenes) sarà possibile trovare vari esempi di descrizioni comando.

![Esempi di descrizione comando](../images/tooltip/MRTK_Tooltip_Examples.png)
