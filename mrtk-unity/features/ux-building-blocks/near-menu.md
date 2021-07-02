---
title: Menu adiacente
description: Panoramica dei tipi di menu near in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, menu vicino,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175657"
---
# <a name="near-menu"></a>Menu adiacente

![Menu vicino](../images/near-menu/MRTK_UX_NearMenu.png)

Near Menu è un controllo UX che fornisce una raccolta di pulsanti o altri componenti dell'interfaccia utente. È mobile intorno al corpo dell'utente e facilmente accessibile in qualsiasi momento. Poiché è associato in modo libero all'utente, non influisce sull'interazione dell'utente con il contenuto di destinazione. L'utente può usare il pulsante "Aggiungi" per bloccare o sbloccare il menu. Il menu può essere afferrato e posizionato in una posizione specifica.

## <a name="interaction-behavior"></a>Comportamento di interazione

- **Tag lungo:** il menu segue l'utente e rimane entro un intervallo di 30-60 cm dall'utente per le interazioni da vicino.
- **Aggiungi:** usando il pulsante "Aggiungi", il menu può essere bloccato a livello mondiale e rilasciato.
- **Afferra e sposta:** il menu è sempre afferrabile e mobile. Indipendentemente dallo stato precedente, il menu verrà aggiunto (bloccato al mondo) quando viene afferrato e rilasciato. Esistono segnali visivi per l'area afferrabile. Vengono rivelati sulla prossimità manuale.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Prefab

I prefab near menu sono progettati per illustrare come usare i vari componenti di MRTK per creare menu per le interazioni da vicino.

- **NearMenu2x4.prefab**
- **NearMenu3x1.prefab**
- **NearMenu3x2.prefab**
- **NearMenu3x3.prefab**
- **NearMenu4x1.prefab**
- **NearMenu4x2.prefab**

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi di prefab near menu nella `NearMenuExamples` scena.

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>Struttura

I prefab near menu sono realizzati con i componenti MRTK seguenti.

- [**Prefab PressableButtonHoloLens2**](button.md)
- [**Raccolta di oggetti Grid:**](object-collection.md)layout a più pulsanti nella griglia
- [**Manipulation Handler (Gestore**](manipulation-handler.md)manipolazione): afferra e sposta il menu
- [**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior (Comportamento del risolutore RadialView: seguimi)(tag-along)

![Prefab menu vicino](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Modalità di personalizzazione

**1. Aggiungere/rimuovere pulsanti**

`ButtonCollection`Nell'oggetto aggiungere o rimuovere pulsanti.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. Aggiornare la raccolta di oggetti Grid**

Fare `Update Collection` clic sul pulsante nel controllo dell'oggetto. `ButtonCollection` Aggiornerà il layout della griglia.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

È possibile configurare il numero di righe usando `Rows` la proprietà della raccolta di oggetti Grid.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. Regolare le dimensioni del backplate**

Regolare le dimensioni dell'oggetto `Quad` `Backplate` nell'oggetto . La larghezza e l'altezza del backplate devono essere `0.032 * [Number of the buttons + 1]` . Ad esempio, se si dispone di 3 x 2 pulsanti, la larghezza del backplate è `0.032 * 4` e l'altezza è `0.032 * 3` . È possibile inserire direttamente questa espressione nel campo di Unity.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- La dimensione predefinita del HoloLens 2 è 3,2x3,2 cm (0,032 m)

## <a name="see-also"></a>Vedere anche

- [**Pulsanti**](button.md)
- [**Controllo Bounds**](bounds-control.md)
- [**Slider**](sliders.md)
- [**Raccolta di oggetti Grid**](object-collection.md)
- [**Gestore di manipolazione**](manipulation-handler.md)
- [**Risolutore RadialView**](solvers/solver.md)
