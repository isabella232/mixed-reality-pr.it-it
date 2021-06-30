---
title: Configurazione della visualizzazione dei limiti
description: Dettagli per configurare il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 0f1a9edd9f9a31e7ba20f630406b299909a4864c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121249"
---
# <a name="configuring-the-boundary-visualization"></a>Configurazione della visualizzazione dei limiti

Il *profilo di visualizzazione dei* limiti offre opzioni per la configurazione dell'aspetto visivo e di altri parametri correlati per il sistema di limiti. Le visualizzazioni dei limiti vengono collegate all'oggetto Playspace di realtà mista nella scena e teletrasportate con l'utente.

## <a name="general-settings"></a>Impostazioni generali

![Impostazioni generali di visualizzazione dei limiti](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>Altezza limite

L'altezza limite indica la distanza sopra il piano del piano in corrispondenza della quale deve essere eseguito il rendering del limite massimo. Il valore predefinito è 3 metri.

## <a name="floor-settings"></a>Impostazioni del piano

![Impostazioni del piano per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationFloorSettings.png)

**Mostra**

Indica se un piano piano deve essere creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione del piano piano.

**Scalabilità**

Indica le dimensioni, in metri, del piano piano da creare. La scala predefinita è 3 metri x 3 metri quadrati.

**Livello fisico**

Livello su cui deve essere impostato il piano piano. Il valore predefinito è *Il livello* predefinito.

## <a name="play-area-settings"></a>Impostazioni dell'area di riproduzione

![Impostazioni dell'area di riproduzione per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**Mostra**

Indica se un rettangolo dell'area di riproduzione viene creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione dell'oggetto area di riproduzione.

**Livello fisico**

Livello su cui deve essere impostata l'area di riproduzione. Il valore predefinito è *Ignora raycast.*

## <a name="tracked-area-settings"></a>Impostazioni dell'area rilevata

![Impostazioni dell'area rilevata per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**Mostra**

Indica se la struttura dell'area tracciata deve essere creata e aggiunta alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione del contorno dell'area tracciata.

**Livello fisico**

Livello su cui deve essere impostata l'area rilevata. Il valore predefinito è *Ignora raycast.*

## <a name="boundary-wall-settings"></a>Impostazioni della barriera limite

![Boundary Visualization Boundary Wall Settings](../images/boundary/BoundaryVisualizationWallSettings.png)

**Mostra**

Indica se i piani delle pareti limite devono essere creati e aggiunti alla scena. Il valore predefinito è false.

**Materiale**

Indica il materiale da usare durante la creazione dei piani delle pareti limite.

**Livello fisico**

Livello su cui devono essere impostate le pareti limite. Il valore predefinito è *Ignora raycast.*

> [!NOTE]
> L'impostazione del componente della barriera limite su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.

## <a name="boundary-ceiling-settings"></a>Impostazioni limite massimo

![Boundary Visualization Boundary Ceiling Settings](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**Mostra**

Indica se un piano limite del limite deve essere creato e aggiunto alla scena. Il valore predefinito è false.

**Materiale**

Indica il materiale da usare durante la creazione del piano limite del limite.

**Livello fisico**

Livello su cui devono essere impostate le pareti limite. Il valore predefinito è *Ignora raycast.*

> [!NOTE]
> L'impostazione del componente limite massimo su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.

## <a name="see-also"></a>Vedere anche

- [Documentazione dell'API Limite](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Sistema di limiti](boundary-system-getting-started.md)
