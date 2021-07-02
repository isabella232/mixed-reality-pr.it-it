---
title: Utilità screenshot
description: Documentazione sull'hopw per usare lo strumento screenshot in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 936126214f9e6d93ccbb871b9c80a2c93acf5a86
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176423"
---
# <a name="screenshot-utility"></a>Utilità screenshot

Spesso acquisire screenshot in Unity per la documentazione e le immagini promozionali può essere un'attività gravosa e l'output spesso non è consigliabile. Qui è dove `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit. Entra in gioco la classe Utilities.Editor.ScreenshotUtility.

La classe ScreenshotUtility consente di acquisire screenshot tramite voci di menu e API pubbliche all'interno dell'editor di Unity. Gli screenshot possono essere acquisiti a varie risoluzioni e con colori chiari trasparenti per l'uso nella semplice composizione post-stampa delle immagini. La creazione di screenshot da una build autonoma non è supportata da questo strumento.

## <a name="taking-screenshots"></a>Screenshot

Gli screenshot possono essere facilmente acquisite nell'editor selezionando **Mixed Reality** Toolkit Utilities Take Screenshot e quindi  >    >    >   selezionando l'opzione desiderata. Assicurarsi che la scheda della finestra del gioco sia visibile se l'acquisizione non è in esecuzione oppure uno screenshot potrebbe non essere salvato.

Per impostazione predefinita, tutti gli screenshot vengono salvati nel percorso della [cache](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)temporanea. Il percorso dello screenshot verrà visualizzato nella console di Unity.

![Voce di menu dell'utilità Screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Screenshot di esempio

Lo screenshot seguente è stato acquisito con l'opzione *"Risoluzione 4x (sfondo trasparente)".* In questo modo viene restituita un'immagine ad alta risoluzione con i pixel normalmente rappresentati dal colore non crittografato salvato come pixel trasparenti. Questa tecnica consente agli sviluppatori di presentare la propria applicazione per lo store o altri media, sovrapponendo questa immagine ad altre immagini.

![Esempio di acquisizione di utilità screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
