---
title: Visualizzazione Mesh spaziale
description: Informazioni sul modo in cui i dispositivi comprendono gli ambienti fisici che usano mesh spaziali.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realtà mista, HoloLens, controlli dell'interfaccia utente, interazione, interfaccia utente, UX, progettazione di UX, interfaccia utente spaziale, interazione spaziale, interfaccia utente 3D, UX 3D, auricolare in realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: ffa13da6762b803ba2a3f370308ac2af65164ecf
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848195"
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
* Per altre informazioni, vedere [MRTK-Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) e [MRTK-Pulse shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).

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
