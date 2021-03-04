---
title: README_AppBar
description: Panoramica sulla barra dell'app in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, barra dell'app,
ms.openlocfilehash: c02d2c851b9bc1cec5154ea6ef89772a686c5e08
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782969"
---
# <a name="app-bar"></a>Barra dell'app

![Barra dell'app](../images/app-bar/MRTK_AppBar_Main.png)

La barra dell'app è un componente dell'interfaccia utente usato insieme allo script di [controllo dei limiti](BoundsControl.md) . Aggiunge i controlli Button a un oggetto con l'intenzione di modificarlo. Utilizzando il pulsante ' Adjust ', l'interfaccia di controllo dei limiti per un oggetto può essere disattivata. Il pulsante "Rimuovi" deve rimuovere l'oggetto dalla scena.

## <a name="how-to-use-app-bar"></a>Come usare la barra dell'app

Trascinare e rilasciare `AppBar` (assets/MRTK/SDK/features/UX/precasers/AppBar/AppBar. prefabricable) nella gerarchia della scena. Nel pannello Inspector del componente, assegnare un oggetto con un controllo Bounds come rettangolo di selezione di *destinazione* a cui aggiungere la barra dell'app.

**Importante:** L'opzione di attivazione del controllo dei limiti per l'oggetto di destinazione deve essere ' Activate manually '.

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Setup 2">
