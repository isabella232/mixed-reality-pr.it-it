---
title: NearMenuUI
description: Panoramica dei tipi di menu near in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, menu vicino,
ms.openlocfilehash: a8e34bb2e0f322e570475c5fbc3c57a8a4c2a602f375e0ac0a36a4444c2c5d3d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199781"
---
# <a name="near-menu"></a>Menu adiacente

![Menu vicino](../images/near-menu/MRTK_UX_NearMenu.png)

Near Menu è un controllo UX che fornisce una raccolta di pulsanti o altri componenti dell'interfaccia utente. È mobile intorno al corpo dell'utente e facilmente accessibile in qualsiasi momento. Poiché è liberamente associato all'utente, non disturba l'interazione dell'utente con il contenuto di destinazione. L'utente può usare il pulsante "Aggiungi" per bloccare/sbloccare il menu. Il menu può essere afferrato e posizionato in una posizione specifica.

## <a name="interaction-behavior"></a>Comportamento dell'interazione

- **Tag-along**: il menu segue l'utente e rimane entro un intervallo di 30-60 cm dall'utente per le interazioni più vicine.
- **Aggiungi:** usando il pulsante "Aggiungi", il menu può essere bloccato a livello mondiale e rilasciato.
- **Grab and move**(Afferra e sposta): il menu è sempre selezionabile e mobile. Indipendentemente dallo stato precedente, il menu verrà aggiunto (world-locked) quando viene afferrato e rilasciato. Esistono segnali visivi per l'area afferrabile. Vengono rivelati sulla prossimità manuale.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Prefab

I prefab near Menu sono progettati per illustrare come usare i vari componenti di MRTK per creare menu per le interazioni near.

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

I prefab near Menu sono realizzati con i componenti MRTK seguenti.

- [**Prefab PressableButtonHoloLens2**](button.md)
- [**Raccolta di oggetti Grid:**](object-collection.md)layout di più pulsanti nella griglia
- [**Gestore di manipolazione:**](manipulation-handler.md)afferrare e spostare il menu
- [**RadialView Solver**](solvers/solver.md): Comportamento Follow Me(tag-along)

![Prefab del menu vicino](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Modalità di personalizzazione

**1. Aggiungere/rimuovere pulsanti**

`ButtonCollection`Nell'oggetto aggiungere o rimuovere pulsanti.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. Aggiornare la raccolta di oggetti Grid**

Fare `Update Collection` clic sul pulsante nel controllo dell'oggetto `ButtonCollection` . Aggiornerà il layout della griglia.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

È possibile configurare il numero di righe usando `Rows` la proprietà della raccolta di oggetti Grid.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. Regolare le dimensioni del backplate**

Regolare le dimensioni `Quad` dell'oggetto `Backplate` in . La larghezza e l'altezza del backplate devono essere `0.032 * [Number of the buttons + 1]` . Ad esempio, se si dispone di 3 x 2 pulsanti, la larghezza del backplate è `0.032 * 4` e l'altezza è `0.032 * 3` . È possibile inserire direttamente questa espressione nel campo di Unity.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- Le dimensioni predefinite del HoloLens 2 sono 3,2x3,2 cm (0,032 m)

## <a name="see-also"></a>Vedi anche

- [**Pulsanti**](button.md)
- [**Controllo Bounds**](bounds-control.md)
- [**Slider**](sliders.md)
- [**Raccolta di oggetti Grid**](object-collection.md)
- [**Gestore di manipolazione**](manipulation-handler.md)
- [**Risolutore RadialView**](solvers/solver.md)
