---
title: Configurazione della visualizzazione dei limiti
description: Dettagli per configurare il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 77bdaedb60700bac27643ae718c795c02e5ee7e7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177093"
---
# <a name="configuring-boundary-visualization"></a>Configurazione della visualizzazione dei limiti

Il *profilo di visualizzazione dei* limiti offre opzioni per la configurazione dell'aspetto visivo e di altri parametri correlati per il sistema di limiti. Le visualizzazioni dei limiti vengono collegate all'oggetto Playspace di realtà mista nella scena e teletrasportate con l'utente.

## <a name="general-settings"></a>Impostazioni generali

![Visualizzazione dei limiti Generale Impostazioni](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>Altezza limite

L'altezza limite indica la distanza sopra il piano del piano in corrispondenza della quale deve essere eseguito il rendering del limite massimo. Il valore predefinito è 3 metri.

## <a name="floor-settings"></a>Impostazioni del piano

![Boundary Visualization Floor Impostazioni](../images/boundary/BoundaryVisualizationFloorSettings.png)

**Mostra**

Indica se un piano piano deve essere creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione del piano piano.

**Scalabilità**

Indica le dimensioni, in metri, del piano piano da creare. La scala predefinita è 3 metri x 3 metri quadrati.

**Livello fisico**

Livello su cui deve essere impostato il piano piano. Il valore predefinito è *Il livello* predefinito.

## <a name="play-area-settings"></a>Impostazioni dell'area di riproduzione

![Area di riproduzione per la visualizzazione dei limiti Impostazioni](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**Mostra**

Indica se un rettangolo dell'area di riproduzione viene creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione dell'oggetto area di riproduzione.

**Livello fisico**

Livello su cui deve essere impostata l'area di riproduzione. Il valore predefinito è *Ignora raycast.*

## <a name="tracked-area-settings"></a>Impostazioni dell'area rilevata

![Area tracciata per la visualizzazione dei limiti Impostazioni](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**Mostra**

Indica se il contorno dell'area tracciata deve essere creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare durante la creazione del contorno dell'area tracciata.

**Livello fisico**

Livello su cui deve essere impostata l'area rilevata. Il valore predefinito è *Ignora raycast.*

## <a name="boundary-wall-settings"></a>Impostazioni della barriera limite

![Limite limite di visualizzazione dei limiti Impostazioni](../images/boundary/BoundaryVisualizationWallSettings.png)

**Mostra**

Indica se i piani delle pareti limite devono essere creati e aggiunti alla scena. Il valore predefinito è false.

**Materiale**

Indica il materiale da usare durante la creazione dei piani delle pareti limite.

**Livello fisico**

Livello su cui devono essere impostate le pareti limite. Il valore predefinito è *Ignora raycast.*

> [!NOTE]
> L'impostazione del componente della barriera limite su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.

## <a name="boundary-ceiling-settings"></a>Impostazioni limite massimo

![Limite massimo limite di visualizzazione Impostazioni](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**Mostra**

Indica se un piano limite deve essere creato e aggiunto alla scena. Il valore predefinito è false.

**Materiale**

Indica il materiale da usare durante la creazione del piano limite del limite.

**Livello fisico**

Livello su cui devono essere impostate le pareti limite. Il valore predefinito è *Ignora raycast.*

> [!NOTE]
> L'impostazione del componente limite massimo su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.

## <a name="see-also"></a>Vedere anche

- [Documentazione dell'API Limite](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Sistema di limiti](boundary-system-getting-started.md)
