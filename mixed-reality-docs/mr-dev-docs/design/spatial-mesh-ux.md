---
title: Visualizzazione Mesh spaziale
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realtà mista, HoloLens, controlli dell'interfaccia utente, interazione, interfaccia utente, UX, progettazione di UX, interfaccia utente spaziale, interazione spaziale, interfaccia utente 3D, UX 3D, auricolare in realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: ec887f73b8561e0a91740d612227411683707364
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703297"
---
# <a name="spatial-mesh"></a>Mesh spaziale

![Mesh spaziale](images/MRTK_PulseShader_SpatialMesh.gif)

Attraverso la visualizzazione Mesh spaziale, l'utente può apprendere in che modo un dispositivo percepisce e riconosce l'ambiente fisico. Oltre a fornire il contesto spaziale, la visualizzazione Mesh spaziale corretta può creare un'esperienza deliziosa e magica.  

## <a name="design-guideline"></a>Linee guida per la progettazione
Poiché è importante consentire all'utente di concentrarsi e interagire con il contenuto, è possibile che la visualizzazione continua e ripetuta della mesh spaziale in background risulti distrazione. Si consiglia di visualizzare l'ambiente in modo sporadico, una sola volta all'avvio iniziale o quando l'utente mostra chiaramente l'intenzione di visualizzare la mesh ambientale selezionando lo spazio di destinazione e il tocco di aria. È possibile osservare questo comportamento nella shell HoloLens.
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualizzazione Mesh spaziale in MRTK (Toolkit realtà mista) per Unity
MRTK fornisce diversi materiali per la visualizzazione Mesh spaziale.

- **MRTK_Wireframe. mat, MRTK_Wireframe. Mat**: materiale mesh spaziale statico predefinito che mostra le strutture mesh senza animazione. Questo materiale è utile a scopo di debug perché mostra le geometrie dell'intera mesh spaziale. Tuttavia, non è consigliabile per la produzione.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. Mat**: questo materiale fornisce un effetto a impulsi animati sulla mesh spaziale. È possibile usare questo materiale per visualizzare l'ambiente in un momento specifico dell'esperienza o in base all'input dell'utente. Vedere la scena **PulseShaderExamples. Unity** per gli esempi.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* Per altri dettagli, vedere [MRTK-Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) e [MRTK-Pulse shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .

<br>

---

## <a name="see-also"></a>Vedere anche

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
