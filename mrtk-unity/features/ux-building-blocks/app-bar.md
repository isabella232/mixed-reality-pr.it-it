---
title: Barra dell'app
description: Panoramica sulla barra dell'app in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, barra delle app,
ms.openlocfilehash: 1ecb43d25a4353ff4c3bd8350efaab877900a5b979cd42d2c8d1cb91ce32ae0c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198278"
---
# <a name="app-bar"></a>Barra dell'app

![Barra dell'app](../images/app-bar/MRTK_AppBar_Main.png)

La barra dell'app è un componente dell'interfaccia utente che viene usato insieme allo script [di controllo dei](bounds-control.md) limiti. Aggiunge i controlli pulsante a un oggetto con la finalità di modificarlo. Usando il pulsante "Regola", l'interfaccia di controllo dei limiti per un oggetto può essere de-/attivata. Il pulsante "Rimuovi" dovrebbe rimuovere l'oggetto dalla scena.

## <a name="how-to-use-app-bar"></a>Come usare la barra dell'app

Trascinare `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) nella gerarchia della scena. Nel pannello di controllo del componente assegnare qualsiasi oggetto con un controllo limiti come rettangolo di selezione di destinazione *per* aggiungere la barra dell'app.

**Importante:** L'opzione di attivazione del controllo dei limiti per l'oggetto di destinazione deve essere "Attiva manualmente".

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
