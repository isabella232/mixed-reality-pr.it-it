---
title: Impostazioni dell'esperienza
description: Documentazione sulle diverse impostazioni dell'esperienza per MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 19d812ccfa9c0317e40dee2b7d03220848782cef955ba859a150b4f4adc8aa99
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203248"
---
# <a name="experience-settings"></a>Impostazioni dell'esperienza

Una delle sfide della creazione dell'interfaccia utente per la realtà mista è l'allineamento tra esperienze diverse. Con MRTK è possibile impostare e per la scena in modo che il comportamento seguente si comporti in modo appropriato `Target Experience Scale` per la scala di `Content Offset` destinazione.

- Contenuto della scena di realtà mista
- Sistema di limiti

  ![Esperienza Impostazioni nel profilo di configurazione MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>Scalabilità dell'esperienza di destinazione

La **scalabilità dell'esperienza di** destinazione specifica l'ambiente per cui è progettata l'esperienza. Può assumere i valori seguenti.

* *OrientationOnly:* esperienza che usa solo l'orientamento del visore ed è allineata alla gravità. L'origine del sistema di coordinate è a livello di testa.
* *Seduti:* un'esperienza progettata per l'uso da seduti. L'origine del sistema di coordinate è a livello di piano.
* *In piedi:* un'esperienza progettata per l'uso in posizione stazionaria. L'origine del sistema di coordinate è a livello di piano.
* *Room:* un'esperienza progettata per supportare lo spostamento in una stanza. L'origine del sistema di coordinate è a livello di piano.
* *Mondo:* un'esperienza progettata per usare e spostarsi nel mondo fisico. L'origine del sistema di coordinate è a livello di testa.

## <a name="content-offset"></a>Offset del contenuto

Questo parametro specifica l'altezza sopra [](scene-content.md) il pavimento per compensare il contenuto della scena di realtà mista quando **Tipo** di allineamento è impostato su Allinea con **scala esperienza**
