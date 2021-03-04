---
title: README_ScrollingObject
description: Descrizione che scorre la raccolta di oggetti in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: dea20e9df9c00207b2a9b1c6b5a893fa357de755
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781552"
---
# <a name="scrolling-object-collection"></a>Scorrimento della raccolta di oggetti

![Scorrimento della raccolta](../../features/Images/ScrollingCollection/MRTK_UX_ScrollingCollection_Main.jpg)

ScrollingObjectCollection è una raccolta di oggetti che scorre in modo nativo gli oggetti 3D. Supporta lo scorrimento di pulsanti stampabili e Interactables, nonché oggetti non interattivi. Questa raccolta supporta l'input sia vicino che lontano. Per usare ScrollingObjectCollection, gli oggetti devono usare lo shader standard MRTK per garantire il corretto funzionamento dell'effetto di ritaglio.

## <a name="getting-started-with-scrolling-object-collection"></a>Introduzione alla raccolta di oggetti di scorrimento

Per praticità, sono disponibili due prefabbricati ScrollingObjectCollection da usare. Una viene configurata per funzionare con 32x92mm PressableButton prefabbricates e l'altra per qualsiasi oggetto in un contenitore 32x32x32mm.

È sufficiente rilasciarle in una scena, aggiungere gli oggetti desiderati e premere "Updatecollection" per completare la configurazione e il layout della raccolta.

### <a name="prerequisites"></a>Prerequisiti

- Tutti gli oggetti nella raccolta devono usare lo shader standard MRTK
- Ogni oggetto nella raccolta deve avere un Collider con un [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) . Tutti i test di collisione sono attualmente eseguiti usando questi Collider; ScrollingObjectCollection non supporta ancora un Collider di backup statico/non in stato di trasferimento.
- Per tutti gli oggetti della raccolta devono essere presenti le stesse dimensioni. è inoltre possibile ottenere risultati imprevisti se gli oggetti non sono centrati in un gameObject.
- Per una superficie facilmente toccabile, le "dimensioni della cella" nella raccolta di scorrimento devono corrispondere alle dimensioni di ogni oggetto nella raccolta.

Sono previsti requisiti aggiuntivi quando si usano i pulsanti:

- PressableButton. ReleaseOnTouch deve essere disabilitato.
- PhysicalPressEventRouter. InteractableOnClick sono più impostati su EventOnClickCompletion o EventOnPress.
- In fase di modifica, ScrollingObjectCollection è in grado di correggere automaticamente questi componenti. Tuttavia, quando si crea un'istanza dinamica dei prefissi o dei componenti, assicurarsi che queste proprietà siano impostate correttamente.

## <a name="how-it-works"></a>Funzionamento

ScrollingObjectCollection sottoscrive se stesso come listener globale per gli eventi di tocco e di puntatore, filtrando gli eventi che corrispondono agli elementi dell'elenco. Inizialmente, la raccolta non esegue alcuna operazione e consente agli eventi di passare agli oggetti figlio, in modo che gli oggetti figlio vengano inseriti e selezionati come previsto. Una volta che ScrollingObjectCollection ha riconsiderato un'interazione come "trascinamento", la raccolta inizia a contrassegnare tutti i eventData successivi come utilizzati e inizia a scorrere l'elenco sull'asse del set.

Quando si usa il tocco, l'elenco continuerà a scorrere fino a quando il PokePointer non ha superato il piano di tocco davanti all'elenco.
