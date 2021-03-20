---
title: ScreenshotUtility
description: Documentazione su Hopw per usare lo strumento screenshot in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4fbd5457dd0af502ddedf30a10482690cd8e1a1d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682084"
---
# <a name="screenshot-utility"></a>Utilità screenshot

Spesso le schermate in Unity per la documentazione e le immagini promozionali possono essere gravose e l'output sembra spesso minore di quanto sia auspicabile. Qui `ScreenshotUtility` entra in gioco la classe (xrif: Microsoft. MixedReality. Toolkit. Utilities. Editor. ScreenshotUtility).

La classe ScreenshotUtility aiuta ad acquisire screenshot tramite voci di menu e API pubbliche nell'editor di Unity. Le schermate possono essere acquisite con diverse risoluzioni e con colori cancellati trasparenti per l'uso in una semplice composizione post di immagini. Lo strumento non supporta l'acquisizione di schermate da una compilazione autonoma.

## <a name="taking-screenshots"></a>Acquisizione di schermate

Le schermate possono essere facilmente acquisite nell'editor selezionando *reality Toolkit->Utilities->acquisire screenshot* e quindi selezionare l'opzione desiderata. Assicurarsi che la scheda della finestra di gioco sia visibile se l'acquisizione non viene riprodotta oppure è possibile che non sia stata salvata una schermata.

Per impostazione predefinita, tutte le schermate vengono salvate nel [percorso della cache temporanea](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), il percorso dello screenshot verrà visualizzato nella console di Unity.

![Voce di menu utilità screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Acquisizione di screenshot di esempio

La schermata seguente è stata acquisita con l'opzione *"risoluzione 4x (sfondo trasparente)"* . Viene così restituita un'immagine ad alta risoluzione con qualsiasi pixel normalmente rappresentato dal colore chiaro salvato come pixel trasparenti. Questa tecnica aiuta gli sviluppatori a presentare le proprie applicazioni per lo Store o altri punti di supporto, sovrapponendo questa immagine sopra le altre immagini.

![Esempio di acquisizione dell'utilità screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
