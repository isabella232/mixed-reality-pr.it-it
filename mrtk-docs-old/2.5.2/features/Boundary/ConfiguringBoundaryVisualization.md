---
title: ConfiguringBoundaryVisualization
description: Dettagli per configurare il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 8af3b540504aeded36d5000411d78b27e73e27a8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695878"
---
# <a name="configuring-the-boundary-visualization"></a>Configurazione della visualizzazione dei limiti

Il *profilo di visualizzazione dei limiti* fornisce opzioni per la configurazione dell'estetica visiva e di altri parametri correlati per il sistema di limiti. Le visualizzazioni dei limiti sono collegate all'oggetto playspace della realtà mista nella scena e si teletrasportano con l'utente.

## <a name="general-settings"></a>Impostazioni generali

![Impostazioni generali visualizzazione limite](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>Altezza limite

L'altezza del limite indica la distanza al di sopra del piano di pavimento in corrispondenza della quale deve essere eseguito il rendering del limite massimo. Il valore predefinito è 3 metri.

## <a name="floor-settings"></a>Impostazioni del piano

![Impostazioni del piano visualizzazione limite](../images/boundary/BoundaryVisualizationFloorSettings.png)

**Mostra**

Indica se un piano di piano deve essere creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da utilizzare durante la creazione del piano di piano.

**Ridimensiona**

Indica la dimensione, in metri, del piano del piano da creare. La scala predefinita è un quadrato da 3 metri x 3 metri.

**Livello di fisica**

Livello sul quale deve essere impostato il piano del piano. Il valore predefinito è il livello *predefinito* .

## <a name="play-area-settings"></a>Impostazioni area di riproduzione

![Impostazioni dell'area di riproduzione della visualizzazione limite](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**Mostra**

Indica se un rettangolo area di riproduzione viene creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da utilizzare quando si crea l'oggetto area di riproduzione.

**Livello di fisica**

Il livello in cui deve essere impostata l'area di riproduzione. Il valore predefinito è il livello *Ignora Raycast* .

## <a name="tracked-area-settings"></a>Impostazioni area rilevata

![Impostazioni area rilevate visualizzazione limite](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**Mostra**

Indica se il contorno dell'area rilevata viene creato e aggiunto alla scena. Il valore predefinito è true.

**Materiale**

Indica il materiale da usare quando si crea il contorno dell'area rilevata.

**Livello di fisica**

Il livello in cui deve essere impostata l'area rilevata. Il valore predefinito è il livello *Ignora Raycast* .

## <a name="boundary-wall-settings"></a>Impostazioni muro limite

![Impostazioni parete limite visualizzazione limite](../images/boundary/BoundaryVisualizationWallSettings.png)

**Mostra**

Indica se devono essere creati e aggiunti alla scena i piani della parete limite. Il valore predefinito è false.

**Materiale**

Indica il materiale da usare quando si creano i piani della barriera limite.

**Livello di fisica**

Livello su cui devono essere impostati i muri limite. Il valore predefinito è il livello *Ignora Raycast* .

> [!NOTE]
> L'impostazione del componente della parete limite su un livello di fisica diverso da *Ignore Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.

## <a name="boundary-ceiling-settings"></a>Impostazioni Ceiling limite

![Impostazioni limite massimo limite visualizzazione limite](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**Mostra**

Indica se è necessario creare un piano di limite massimo e aggiungerlo alla scena. Il valore predefinito è false.

**Materiale**

Indica il materiale da usare quando si crea il piano limite massimo.

**Livello di fisica**

Livello su cui devono essere impostati i muri limite. Il valore predefinito è il livello *Ignora Raycast* .

> [!NOTE]
> Impostando il componente Ceiling limite su un livello di fisica diverso da *Ignore Raycast* , è possibile impedire agli utenti di interagire con gli oggetti all'interno della scena.

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API limite](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Sistema di limiti](BoundarySystemGettingStarted.md)
