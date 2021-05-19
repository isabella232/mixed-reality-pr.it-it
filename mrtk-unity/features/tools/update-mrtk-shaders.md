---
title: Strumento di aggiornamento shader
description: Documentazione su come aggiornare gli shader standard MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ed9f9fa5e6337850f31ecce9d07bc82a8ea12060
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145137"
---
# <a name="updating-shaders"></a>Aggiornamento di shader

A partire dalla versione 2.6.0, il controllo delle versioni degli shader MRTK viene effettuato tramite MRTK. File Shaders.sentinel. Quando si esegue l'aggiornamento a una nuova versione di MRTK, potrebbe essere visualizzato il messaggio seguente.

![Richiesta di aggiornamento shader](../images/tools/UpdateShaderPrompt.png)

Selezionando **Sì** si indica a MRTK di sovrascrivere il contenuto degli shader  >  **MRTK**  >  **asset con** la versione più recente. Se **si seleziona No,** i file correnti verranno mantenuti. **Ignora** creerà un file ( `IgnoreUpdateCheck.sentinel` ) in **Asset**  >  **MRTK** Shaders , che elimina  >  i controlli di aggiornamento dello shader futuri.

> [!IMPORTANT]
> Quando si sovrascriveno i file shader, tutte le modifiche personalizzate andranno perse. Assicurarsi di eseguire il backup di tutti i file shader modificati prima dell'aggiornamento.
>
> Se il progetto è stato configurato per l'uso della pipeline di rendering universale (URP), in precedenza Lightweight Render Pipeline (LWRP), eseguire di nuovo **Mixed Reality Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.

In è anche possibile verificare la disponibilità di aggiornamenti dello shader in qualsiasi momento usando **Mixed Reality Toolkit** Utilities Check for Shader Updates (Verifica aggiornamenti shader) sulla barra dei menu  >    >   dell'editor di Unity.

![Verificare la disponibilità di aggiornamenti dello shader](../images/tools/ShaderUpdateMenu.png)

**Controlla aggiornamenti shader ignora** il `IgnoreUpdateCheck.sentinel` file e consente l'aggiornamento dello shader su richiesta.

> [!NOTE]
> La verifica degli aggiornamenti dello shader non è necessaria quando si importano i file .unitypackage MRTK.
