---
title: ShaderUpdateTool
description: Documentazione su come aggiornare gli shader standard di MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e5ae9f12dfe4af899ae3d25af6dd0f076744b5c5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689381"
---
# <a name="updating-shaders"></a>Aggiornamento degli shader

A partire dalla versione 2.6.0, viene eseguito il controllo delle versioni degli shader MRTK tramite MRTK. File shaders. Sentinel. Quando si esegue l'aggiornamento a una nuova versione di MRTK, è possibile che venga visualizzato il messaggio seguente.

![Richiedi aggiornamento shader](../images/tools/UpdateShaderPrompt.png)

Selezionando **Sì si** indica a MRTK di sovrascrivere il contenuto degli **Asset**  >  **MRTK**  >  **shader** con la versione più recente. Se si seleziona No, i file correnti **non** vengono conservati. **Ignora** creerà un file ( `IgnoreUpdateCheck.sentinel` ) in **Asset**  >  **MRTK**  >  **shaders**, che eliminerà i controlli di aggiornamento shader futuri.

> [!IMPORTANT]
> Quando si sovrascrivono i file shader, le eventuali modifiche personalizzate andranno perse. Assicurarsi di eseguire il backup dei file shader modificati prima dell'aggiornamento.
>
> Se il progetto è stato configurato per l'uso della pipeline di rendering universale (URP), in precedenza Lightweight render pipeline (LWRP) **, eseguire** di nuovo l' >  >
>  **aggiornamento di MRTK standard shader per la pipeline di rendering semplificata**.

È anche possibile verificare la disponibilità di aggiornamenti dello shader in qualsiasi momento usando le utilità del **Toolkit di realtà mista**  >    >  **per verificare la presenza di aggiornamenti dello shader** sulla barra dei menu dell'editor di Unity.

![Verifica aggiornamenti shader](../images/tools/ShaderUpdateMenu.png)

**Controllare se gli aggiornamenti dello shader** ignorano il `IgnoreUpdateCheck.sentinel` file e consentono l'aggiornamento su richiesta dello shader.

> [!NOTE]
> Il controllo degli aggiornamenti dello shader non è obbligatorio quando si importano i file MRTK. file unitypackage Tools.
