---
title: Ancora
description: Descrizione per i controlli di ancoraggio.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: deb5cbd207befd9e941c6556d615523b0af11ca3
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685644"
---
# <a name="dock"></a>Ancora

![Ancora](../images/dock/MRTK_UX_Dock_Main.png)

Questo controllo consente lo spostamento di oggetti all'interno e all'esterno di posizioni predeterminate, per la creazione di tavolozze, scaffali e barre di spostamento.

## <a name="features"></a>Funzionalità

- Supporta un numero qualsiasi di posizioni e layout di ancoraggio (funziona perfettamente con [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) )
- Gli oggetti ancorati si spostano automaticamente per creare spazio per i nuovi oggetti
- Gli oggetti vengono ridimensionati per adattarsi allo spazio ancorato, quindi vengono ridimensionati in base alla posizione originale quando vengono trascinati.

## <a name="getting-started-with-dock"></a>Introduzione a Dock

- Creare una GameObject con il componente Dock e aggiungere alcuni elementi figlio GameObject.
- Aggiungere il componente impostata su DockPosition a ognuno degli elementi figlio.
- Aggiungere il componente ancorabile a un numero qualsiasi di oggetti nella scena per consentirne l'ancoraggio. Devono avere anche il [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) componente e un Collider.
- *Facoltativo:* usare un [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) al dock per il layout automatico del DockPositions.

### <a name="prerequisites"></a>Prerequisiti

- Ogni oggetto ancorabile deve avere un Collider con [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) o [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .
- Se si vuole che un oggetto venga avviato ancorato quando viene caricata la scena, assegnarlo alla proprietà dell'oggetto ancorato di impostata su DockPosition.

## <a name="how-it-works"></a>Funzionamento

Il componente ancorabile si basa su eventi di manipolazione per consentire l'ancoraggio e la disattivazione di oggetti trascinati in posizioni specifiche. Il posizionamento è determinato dal impostata su DockPosition attivato sovrapposto più vicino all'oggetto trascinato, quindi entrambi gli oggetti devono avere Colliders affinché il trigger venga attivato.
