---
title: Slate
description: Documentazione su Slate in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Slate,
ms.openlocfilehash: 6bc1f18c71367ce05aadae0ff3f8aa51fd17d10c943022525fc5043d8d7989a2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224025"
---
# <a name="slate"></a>Slate

![Slate](../images/slate/MRTK_Slate_Main.png)

Il prefab Slate offre un controllo di stile finestra sottile per la visualizzazione di contenuto 2D, ad esempio testo normale o articoli che includono supporti. Offre una barra del titolo afferrabile e la *funzionalità Seguimi* *e chiudi.* È possibile scorrere la finestra del contenuto tramite l'input manuale articolato.

## <a name="how-to-use-a-slate-control"></a>Come usare un controllo slate

Un controllo slate è costituito dai seguenti elementi:

* **TitleBar**: l'intera barra del titolo nella parte superiore dello slate.
* **Titolo:** area del titolo sul lato sinistro della barra del titolo.
* **Pulsanti**: area del pulsante sul lato destro della barra del titolo.
* **BackPlate:** lato posteriore dello slate.
* **ContentQuad:** il contenuto viene assegnato come materiale. L'esempio usa un materiale di esempio "PanContent".

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure in the Unity editor">

## <a name="bounds-control"></a>Controllo Limiti

Un controllo slate contiene uno script di controllo dei limiti per il ridimensionamento e la rotazione. Per altre informazioni sul controllo dei limiti, vedere la [pagina dei controlli dei](bounds-control.md) limiti.

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>Pulsanti

Uno slate standard offre due pulsanti come impostazione predefinita nella parte superiore destra della barra del titolo:

* **Seguimi:** attiva/disattiva i componenti di un risolutore orbitale per fare in modo che l'oggetto ardesia segua l'utente.
* **Close**: disabilita l'oggetto slate.

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Button">

## <a name="scripts"></a>Script

In generale, lo script deve essere collegato a qualsiasi oggetto destinato `NearInteractionTouchable.cs` a ricevere eventi di tocco da `IMixedRealityTouchHandler` .

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Structure">

* `HandInteractionPan.cs` Questo script gestisce l'input manuale articolato per toccare e spostare il contenuto nell'oggetto *ContentQuad dello* slate.

* `HandInteractionPanZoom.cs`: oltre all'interazione di panoramica, questo script supporta lo zoom a due mani.

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zooming">
