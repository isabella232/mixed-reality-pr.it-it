---
title: Slate
description: Documentazione su Slate in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Slate,
ms.openlocfilehash: 3275cfdb96416be10853e4fdad98f406da677194
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689131"
---
# <a name="slate"></a>Slate

![Slate](../images/slate/MRTK_Slate_Main.png)

La prefabbricata dello Slate offre un controllo dello stile della finestra sottile per la visualizzazione di contenuto 2D, ad esempio testo normale o articoli che includono supporti. Offre una barra del titolo afferrabile, oltre a *seguire* e *chiudere* la funzionalità. È possibile scorrere la finestra del contenuto tramite input della mano articolata.

## <a name="how-to-use-a-slate-control"></a>Come usare un controllo Slate

Un controllo Slate è costituito dagli elementi seguenti:

* **Barra** del titolo: l'intera barra del titolo nella parte superiore dello Slate.
* **Title**: area del titolo sul lato sinistro della barra del titolo.
* **Buttons**: area del pulsante sul lato destro della barra del titolo.
* **Backplate**: il lato posteriore dello Slate.
* **ContentQuad**: il contenuto viene assegnato come materiale. Nell'esempio viene utilizzato un materiale di esempio ' PanContent '.

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure in the Unity editor">

## <a name="bounds-control"></a>Controllo dei limiti

Un controllo Slate contiene uno script di controllo dei limiti per la scala e la rotazione. Per ulteriori informazioni sul controllo dei limiti, vedere la pagina relativa al [controllo dei limiti](bounds-control.md) .

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>Pulsanti

Uno slate standard offre due pulsanti come predefiniti nella parte superiore destra della barra del titolo:

* **Follow me**: Abilita o imposta i componenti del Risolutore orbitali per fare in modo che l'oggetto Slate segua l'utente.
* **Close**: Disabilita l'oggetto Slate.

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Button">

## <a name="scripts"></a>Script

In generale, lo `NearInteractionTouchable.cs` script deve essere collegato a qualsiasi oggetto destinato a ricevere eventi di tocco da `IMixedRealityTouchHandler` .

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Structure">

* `HandInteractionPan.cs` Questo script gestisce l'input della mano articolata per toccare e muovere il contenuto nel *ContentQuad* dello Slate.

* `HandInteractionPanZoom.cs`: Oltre all'interazione di panoramica, questo script supporta lo zoom a due bit.

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zooming">
