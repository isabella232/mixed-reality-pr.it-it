---
title: NearMenuUI
description: Panoramica vicino ai tipi di menu in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, menu near,
ms.openlocfilehash: de420d6365516bf37604095b6cdc786e566e4652
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782190"
---
# <a name="near-menu"></a>Menu adiacente

![Near menu UX](../images/near-menu/MRTK_UX_NearMenu.png)

Near menu è un controllo UX che fornisce una raccolta di pulsanti o altri componenti dell'interfaccia utente. Il corpo dell'utente è fluttuante e facilmente accessibile in qualsiasi momento. Poiché è a regime di controllo libero, l'interazione dell'utente con il contenuto di destinazione non viene disturbata. L'utente può utilizzare il pulsante "Aggiungi" per bloccare/sbloccare il menu. Il menu può essere afferrato e posizionato in una posizione specifica.

## <a name="interaction-behavior"></a>Comportamento interazione

- **Tag-along**: il menu segue e rimane entro 30-60cm dall'utente per le interazioni near.
- **Pin**: usando il pulsante "pin", il menu può essere bloccato e rilasciato in tutto il mondo.
- **Acquisisci e sposta**: il menu è sempre accessibile e mobile. Indipendentemente dallo stato precedente, il menu verrà bloccato (con blocco internazionale) quando viene catturato e rilasciato. Sono disponibili segnali visivi per l'area di acquisizione. Vengono rivelate sulla prossimità.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu">

## <a name="prefabs"></a>Prefabbricati

I prefissi dei menu near sono progettati per illustrare come usare i vari componenti di MRTK per compilare menu per le interazioni near.

- **NearMenu2x4. prefabbricate**
- **NearMenu3x1. prefabbricate**
- **NearMenu3x2. prefabbricate**
- **NearMenu3x3. prefabbricate**
- **NearMenu4x1. prefabbricate**
- **NearMenu4x2. prefabbricate**

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi di prefabbricati di menu near nella `NearMenuExamples` scena.

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>Struttura

I prefabbricati di menu near vengono creati con i componenti MRTK seguenti.

- [**PressableButtonHoloLens2**](Button.md) prefabbricato
- [**Raccolta di oggetti Grid**](ObjectCollection.md): layout di più pulsanti nella griglia
- [**Gestore di manipolazione**](ManipulationHandler.md): selezionare e spostare il menu
- [**RadialView Solver**](solvers/Solver.md): comportamento follow me (Tag-Along)

![Prefabbricato menu vicino](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Modalità di personalizzazione

**1. pulsanti Aggiungi/Rimuovi**

In `ButtonCollection` oggetto, Aggiungi o rimuovi pulsanti.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. aggiornare la raccolta di oggetti Grid**

Fare clic sul `Update Collection` pulsante nel controllo dell' `ButtonCollection` oggetto. Il layout della griglia verrà aggiornato.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custom 1">

È possibile configurare il numero di righe utilizzando `Rows` la proprietà della raccolta di oggetti Grid.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu custome 2">

**3. regolare le dimensioni del backplate**

Regolare le dimensioni dell' `Quad` oggetto sotto `Backplate` . La larghezza e l'altezza del backplate devono essere `0.032 * [Number of the buttons + 1]` . Se, ad esempio, si dispone di 3 pulsanti x 2, la larghezza della contropiastra è `0.032 * 4` e l'altezza è `0.032 * 3` . È possibile inserire direttamente questa espressione nel campo di Unity.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near menu customer 3">

- Le dimensioni predefinite del pulsante HoloLens 2 sono 3,2 x 3,2 cm (0.032 m)

## <a name="see-also"></a>Vedi anche

- [**Pulsanti**](Button.md)
- [**Controllo dei limiti**](BoundsControl.md)
- [**Slider**](Sliders.md)
- [**Raccolta di oggetti Grid**](ObjectCollection.md)
- [**Gestore di manipolazione**](ManipulationHandler.md)
- [**Risolutore RadialView**](solvers/Solver.md)
