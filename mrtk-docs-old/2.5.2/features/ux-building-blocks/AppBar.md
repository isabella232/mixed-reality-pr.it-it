---
title: README_AppBar
description: Panoramica sulla barra dell'app in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, barra dell'app,
ms.openlocfilehash: ecf6886713565243f08227a1ad4f097fb1fb121e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691148"
---
# <a name="app-bar"></a>Barra dell'app

![Barra dell'app](../images/app-bar/MRTK_AppBar_Main.png)

La barra dell'app è un componente dell'interfaccia utente usato insieme allo script di [controllo dei limiti](BoundsControl.md) . Aggiunge i controlli Button a un oggetto con l'intenzione di modificarlo. Utilizzando il pulsante ' Adjust ', l'interfaccia di controllo dei limiti per un oggetto può essere disattivata. Il pulsante "Rimuovi" deve rimuovere l'oggetto dalla scena.

## <a name="how-to-use-app-bar"></a>Come usare la barra dell'app

Trascinare e rilasciare `AppBar` (assets/MRTK/SDK/features/UX/precasers/AppBar/AppBar. prefabricable) nella gerarchia della scena. Nel pannello Inspector del componente, assegnare un oggetto con un controllo Bounds come rettangolo di selezione di *destinazione* a cui aggiungere la barra dell'app.

**Importante:** L'opzione di attivazione del controllo dei limiti per l'oggetto di destinazione deve essere ' Activate manually '.

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Setup 2">
