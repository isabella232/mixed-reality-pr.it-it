---
title: Visualizzazione della mesh spaziale
description: Informazioni sulle linee guida di progettazione e sulla comprensione dell'ambiente fisico con la visualizzazione della mesh spaziale in MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realtà mista, HoloLens, controlli dell'interfaccia utente, interazione, interfaccia utente, esperienza utente, progettazione dell'esperienza utente, interfaccia utente spaziale, interazione spaziale, interfaccia utente 3D, esperienza utente 3D, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: 7fcba586f55e6131235d031327da131aa8ba6c97958e4ac282a8f8d048d37992
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216287"
---
# <a name="spatial-mesh"></a>Mesh spaziale

![Mesh spaziale](images/MRTK_PulseShader_SpatialMesh.gif)

Gli utenti apprendono come un dispositivo percepisca e comprendi l'ambiente fisico tramite la visualizzazione della mesh spaziale. Una corretta visualizzazione della mesh spaziale può creare un'esperienza divertente e divertente fornendo al tempo stesso il contesto spaziale.  

## <a name="design-guideline"></a>Linee guida per la progettazione

È importante consentire all'utente di concentrarsi e interagire con il contenuto. La visualizzazione continua della mesh spaziale in background può distrarre. È consigliabile visualizzare l'ambiente solo una volta nel lancio iniziale o quando l'utente mostra chiaramente di voler visualizzare la mesh ambientale selezionando come destinazione lo spazio e toccando l'aria. È possibile osservare questo comportamento nella Portale realtà mista.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualizzazione della mesh spaziale in MRTK (Mixed Reality Toolkit) per Unity

MRTK fornisce diversi materiali per la visualizzazione della mesh spaziale.

- **MRTK_Wireframe.mat, MRTK_Wireframe.mat:** materiale mesh spaziale statica predefinito, che mostra i contorni della mesh senza animazione. Questo materiale è utile a scopo di debug perché mostra tutte le geometrie della mesh spaziale. Tuttavia, non è consigliabile per la produzione.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.mat:** questo materiale offre un effetto di pulsazione animato sulla mesh spaziale. È possibile usare questo materiale per visualizzare l'ambiente in un momento specifico o nell'input di tocco dell'utente. Per gli esempi, vedere la **scena PulseShaderExamples.unity.**
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* Per altre informazioni, vedere [MRTK - Spatial Awareness (MRTK - Consapevolezza](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) [spaziale) e MRTK - Pulse Shader (MRTK - Pulse Shader).](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader)

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