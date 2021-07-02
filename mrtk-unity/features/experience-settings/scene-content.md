---
title: Contenuto della scena di realtà mista
description: Documentazione sul componente contenuto della scena di realtà mista
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177340"
---
# <a name="mixed-reality-scene-content"></a>Contenuto della scena di realtà mista

Quando si aggiunge MRTK a una scena, viene `MixedRealitySceneContent` creato un gameobject. Questo oggetto funge da luogo dedicato in cui posizionare e creare un'istanza del contenuto di realtà mista per garantire la scalabilità appropriata in molte esperienze diverse. Il gameobject ha un monobehavior **MixedRealitySceneContent** equivalente, che può essere configurato tramite il **parametro Alignment Type.** Questo parametro può assumere i valori seguenti.

* *AlignWithExperienceScale:* allinea il contenuto  in base alla scala dell'esperienza di destinazione e **all'offset** del contenuto impostati nella proprietà [Experience Impostazioni](experience-settings.md)
* *AlignWithHeadHeight:* allinea il contenuto alla posizione y della testa dell'utente, ovvero alla posizione della fotocamera principale.


  ![Oggetto contenuto scena realtà mista creato nell'editor](../images/experience-settings/MixedRealitySceneContent.png)
