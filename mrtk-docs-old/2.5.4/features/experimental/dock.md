---
title: Ancora
description: Descrizione per i controlli Dock.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212769"
---
# <a name="dock"></a>Ancora

![Ancora](../images/dock/MRTK_UX_Dock_Main.png)

Questo controllo consente di spostare oggetti da e verso posizioni predeterminate per creare tavolozze, scaffali e barre di spostamento.

## <a name="features"></a>Funzionalità

- Supporta un numero qualsiasi di posizioni di ancoraggio e layout (funziona bene con [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) )
- Gli oggetti ancorati si spostano automaticamente per creare spazio per i nuovi oggetti
- Gli oggetti vengono ridimensionati in base allo spazio ancorato, quindi vengono ridimensionati nella posizione originale quando vengono trascinati.

## <a name="getting-started-with-dock"></a>Introduzione al Dock

- Crea un GameObject con il componente Dock e aggiungi alcuni GameObject figlio.
- Aggiungere il componente DockPosition a ognuno degli elementi figlio.
- Aggiungere il componente Dockable a un numero qualsiasi di oggetti nella scena per consentire l'ancoraggio. Devono avere anche il [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) componente e un collisore.
- *Facoltativo:* usare un oggetto per dock per impostare automaticamente il [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) disposizione degli elementi DockPosition.

### <a name="prerequisites"></a>Prerequisiti

- Ogni oggetto ancorabile deve avere un collisore con o [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .
- Se vuoi che un oggetto inizi Ancorato quando la scena viene caricata, assegnalo alla proprietà dell'oggetto ancorato di dockPosition.

## <a name="how-it-works"></a>Funzionamento

Il componente Dockable si basa su eventi di manipolazione per consentire l'ancoraggio e l'annullamento dell'ancoraggio degli oggetti trascinati in posizioni specifiche. La posizione è determinata dalla proprietà DockPosition attivata sovrapposta più vicina all'oggetto trascinato, quindi entrambi gli oggetti devono avere collisori affinché il trigger si attivi.
