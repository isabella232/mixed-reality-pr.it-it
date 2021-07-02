---
title: Impostazioni dell'esperienza
description: Documentazione sulle diverse impostazioni dell'esperienza per MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177353"
---
# <a name="experience-settings"></a>Impostazioni dell'esperienza

Una delle sfide della creazione dell'interfaccia utente per la realtà mista è l'allineamento tra esperienze diverse. Con MRTK, è possibile impostare e per la scena. Il comportamento seguente verrà configurato in modo appropriato per `Target Experience Scale` `Content Offset` la scala di destinazione.

- Contenuto della scena di realtà mista
- Sistema di limiti

  ![Esperienza Impostazioni nel profilo di configurazione di MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>Scalabilità dell'esperienza di destinazione

La **scalabilità dell'esperienza** di destinazione specifica l'ambiente per cui è progettata l'esperienza. Può assumere i valori seguenti.

* *OrientationOnly:* esperienza che usa solo l'orientamento del visore VR ed è allineata alla gravità. L'origine del sistema di coordinate si trova al livello della testa.
* *Seated :* un'esperienza progettata per l'uso da posti a parte. L'origine del sistema di coordinate è a livello di piano.
* *In piedi:* un'esperienza progettata per l'uso permanente. L'origine del sistema di coordinate è a livello di piano.
* *Room:* esperienza progettata per supportare lo spostamento in una stanza. L'origine del sistema di coordinate è a livello di piano.
* *Mondo:* un'esperienza progettata per usare e spostarsi nel mondo fisico. L'origine del sistema di coordinate si trova al livello della testa.

## <a name="content-offset"></a>Offset del contenuto

Questo parametro specifica l'altezza al [](scene-content.md) di sopra del piano per eseguire l'offset del contenuto della scena di realtà mista quando Tipo di **allineamento** è impostato su Allinea con **scala dell'esperienza**
