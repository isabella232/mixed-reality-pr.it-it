---
title: Utilità screenshot
description: Documentazione sull'hopw per l'uso dello strumento screenshot in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f3e06258f49ca01b37872b9ee462be7fc68651f9ef379ba2d66bb4e9e2796463
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221437"
---
# <a name="screenshot-utility"></a>Utilità screenshot

Spesso acquisire screenshot in Unity per la documentazione e le immagini promozionali può essere un'attività difficile e l'output è spesso meno auspicabile. Qui è dove `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit. Entra in gioco la classe Utilities.Editor.ScreenshotUtility.

La classe ScreenshotUtility consente di acquisire screenshot tramite voci di menu e API pubbliche all'interno dell'editor di Unity. Gli screenshot possono essere acquisiti a diverse risoluzioni e con colori chiari trasparenti per l'uso nella semplice composizione post-composizione delle immagini. La creazione di screenshot da una build autonoma non è supportata da questo strumento.

## <a name="taking-screenshots"></a>Screenshot

È possibile acquisire facilmente gli screenshot nell'editor selezionando **Mixed Reality** Toolkit Utilities Take Screenshot (Acquisisci screenshot utilità di realtà mista) e quindi  >    >    >   selezionando l'opzione desiderata. Assicurarsi che la scheda della finestra del gioco sia visibile se l'acquisizione non è in riproduzione o se non è possibile salvare uno screenshot.

Per impostazione predefinita, tutti gli screenshot vengono salvati nel percorso della [cache](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)temporanea. Il percorso dello screenshot verrà visualizzato nella console di Unity.

![Screenshot della voce di menu dell'utilità](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Acquisizione di screenshot di esempio

Lo screenshot seguente è stato acquisito con *l'opzione "Risoluzione 4x (sfondo trasparente)".* Viene restituita un'immagine ad alta risoluzione con i pixel normalmente rappresentati dal colore non crittografato salvato come pixel trasparenti. Questa tecnica consente agli sviluppatori di presentare la propria applicazione per lo store o altri media, sovrapponendo questa immagine ad altre immagini.

![Screenshot dell'esempio di acquisizione dell'utilità](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
