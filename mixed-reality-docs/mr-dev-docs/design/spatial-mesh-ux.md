---
title: Visualizzazione Mesh spaziale
description: Informazioni sulle linee guida di progettazione e sulla comprensione dell'ambiente fisico con la visualizzazione Mesh spaziale in MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realtà mista, HoloLens, controlli dell'interfaccia utente, interazione, interfaccia utente, UX, progettazione di UX, interfaccia utente spaziale, interazione spaziale, interfaccia utente 3D, UX 3D, auricolare in realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: 5e8ffbb90b1143cd4e11bf45a889c11c233232df
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759807"
---
# <a name="spatial-mesh"></a>Mesh spaziale

![Mesh spaziale](images/MRTK_PulseShader_SpatialMesh.gif)

Gli utenti apprenderanno in che modo un dispositivo percepisce e riconosce l'ambiente fisico attraverso la visualizzazione Mesh spaziale. Una visualizzazione Mesh spaziale corretta può creare un'esperienza deliziosa e magica e fornire contesto spaziale.  

## <a name="design-guideline"></a>Linee guida per la progettazione

È importante consentire all'utente di concentrarsi e interagire con il contenuto. La visualizzazione continua della mesh spaziale in background può essere distrazione. Si consiglia di visualizzare l'ambiente sporadicamente, solo una volta all'avvio iniziale o quando l'utente mostra chiaramente che desiderano visualizzare la mesh ambientale selezionando lo spazio per l'uso e il tocco di aria. È possibile osservare questo comportamento nel portale per la realtà mista.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualizzazione Mesh spaziale in MRTK (Toolkit realtà mista) per Unity

MRTK fornisce diversi materiali per la visualizzazione Mesh spaziale.

- **MRTK_Wireframe. mat, MRTK_Wireframe. Mat**: materiale mesh spaziale statico predefinito, che mostra le strutture mesh senza animazione. Questo materiale è utile a scopo di debug perché mostra le geometrie dell'intera mesh spaziale. Tuttavia, non è consigliabile per la produzione.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. Mat**: questo materiale fornisce un effetto a impulsi animati sulla mesh spaziale. È possibile usare questo materiale per visualizzare l'ambiente in un momento specifico o in base all'input del rubinetto dell'utente. Vedere la scena **PulseShaderExamples. Unity** per gli esempi.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* Per altre informazioni, vedere [MRTK-Spatial Awareness](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md) e [MRTK-Pulse shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/pulse-shader.md).

<br>

---

## <a name="see-also"></a>Vedi anche

* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)
