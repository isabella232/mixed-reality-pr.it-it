---
title: Configurazione diBoundaryVisualization
description: Dettagli per configurare il sistema boundary in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: b8aa53307da37b558a1b844a83c5baa8cffcc2868056ad68d35336b23bfbe43b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195258"
---
# <a name="configuring-the-boundary-visualization"></a>Configurazione della visualizzazione dei limiti

Profilo *di visualizzazione dei limiti* offre opzioni per la configurazione dell'aspetto visivo e di altri parametri correlati per il sistema Boundary. Le visualizzazioni dei limiti vengono collegate all'oggetto Playspace di realtà mista nella scena e teletrasportate con l'utente.

## <a name="general-settings"></a>Impostazioni generali

![Visualizzazione dei limiti Generale Impostazioni](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>Altezza limite

L'altezza del limite indica la distanza sopra il piano terra in cui deve essere eseguito il rendering del controsoffitto limite. Il valore predefinito è 3 metri.

## <a name="floor-settings"></a>Impostazioni del piano

![Riquadro di visualizzazione dei limiti Impostazioni](../images/boundary/BoundaryVisualizationFloorSettings.png)

**Mostra**

Indica se un piano piano deve essere creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione del piano terra.

**Scalabilità**

Indica le dimensioni, in metri, del piano da creare. La scala predefinita è un quadrato di 3 metri x 3 metri.

**Livello fisico**

Livello su cui deve essere impostato il piano terra. Il valore predefinito è *Livello* predefinito.

## <a name="play-area-settings"></a>Impostazioni dell'area di riproduzione

![Area di riproduzione per la visualizzazione dei limiti Impostazioni](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**Mostra**

Indica se un rettangolo dell'area di riproduzione viene creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione dell'oggetto area di riproduzione.

**Livello fisico**

Livello su cui deve essere impostata l'area di riproduzione. Il valore predefinito è *Il livello Ignora Raycast.*

## <a name="tracked-area-settings"></a>Impostazioni dell'area rilevata

![Visualizzazione dei limiti Area tracciata Impostazioni](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**Mostra**

Indica se la struttura dell'area tracciata deve essere creata e aggiunta alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione della struttura dell'area tracciata.

**Livello fisico**

Livello su cui deve essere impostata l'area tracciata. Il valore predefinito è *Il livello Ignora Raycast.*

## <a name="boundary-wall-settings"></a>Impostazioni della parete limite

![Boundary Visualization Boundary Wall Impostazioni](../images/boundary/BoundaryVisualizationWallSettings.png)

**Mostra**

Indica se i piani della parete limite devono essere creati e aggiunti alla scena. Il valore predefinito è false.

**Materiale**

Indica il materiale da usare durante la creazione dei piani della parete limite.

**Livello fisico**

Livello su cui devono essere impostati i limiti. Il valore predefinito è *Il livello Ignora Raycast.*

> [!NOTE]
> L'impostazione del componente della parete limite su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.

## <a name="boundary-ceiling-settings"></a>Impostazioni del limite massimo

![Limite limite visualizzazione limite Impostazioni](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**Mostra**

Indica se un piano limite deve essere creato e aggiunto alla scena. Il valore predefinito è false.

**Materiale**

Indica il materiale che deve essere usato durante la creazione del piano del controsoffitto limite.

**Livello fisico**

Livello su cui devono essere impostati i limiti. Il valore predefinito è *Il livello Ignora Raycast.*

> [!NOTE]
> L'impostazione del componente limite massimo su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API Boundary](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Sistema di limiti](boundary-system-getting-started.md)
