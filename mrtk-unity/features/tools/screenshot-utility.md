---
title: Utilità screenshot
description: Documentazione sull'hopw per usare lo strumento screenshot in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 59bf0df2a32030281c8bf0a1a8574b4dd9bf4607
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143793"
---
# <a name="screenshot-utility"></a>Utilità screenshot

Spesso acquisire screenshot in Unity per la documentazione e le immagini promozionali può essere oneroso e l'output spesso non è consigliabile. È qui che entra in gioco la classe `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility).

La classe ScreenshotUtility consente di acquisire screenshot tramite voci di menu e API pubbliche all'interno dell'editor di Unity. Gli screenshot possono essere acquisiti a varie risoluzioni e con colori chiari trasparenti per l'uso nella semplice composizione post-stampa delle immagini. La creazione di screenshot da una build autonoma non è supportata da questo strumento.

## <a name="taking-screenshots"></a>Screenshot

È possibile acquisire facilmente gli screenshot nell'editor selezionando *Mixed Reality Toolkit->Utilities->Screenshot e* quindi selezionando l'opzione desiderata. Assicurarsi che la scheda della finestra del gioco sia visibile se l'acquisizione non è in esecuzione oppure uno screenshot potrebbe non essere salvato.

Per impostazione predefinita, tutti gli screenshot vengono salvati nel percorso della [cache](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)temporanea. Il percorso dello screenshot verrà visualizzato nella console di Unity.

![Voce di menu dell'utilità Screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Screenshot di esempio

Lo screenshot seguente è stato acquisito con l'opzione *"Risoluzione 4x (sfondo trasparente)".* In questo modo viene restituita un'immagine ad alta risoluzione con i pixel normalmente rappresentati dal colore non crittografato salvato come pixel trasparenti. Questa tecnica consente agli sviluppatori di presentare la propria applicazione per lo store o altri media, sovrapponendo questa immagine ad altre immagini.

![Esempio di acquisizione di utilità screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
