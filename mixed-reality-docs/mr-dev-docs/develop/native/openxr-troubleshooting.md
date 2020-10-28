---
title: Risoluzione dei problemi di OpenXR
description: Risolvere i problemi delle applicazioni OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware, risoluzione dei problemi
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903097"
---
# <a name="openxr-troubleshooting"></a>Risoluzione dei problemi di OpenXR

Di seguito sono riportati alcuni suggerimenti per la risoluzione dei problemi durante lo sviluppo di un'app OpenXR con la realtà mista di Windows OpenXR Runtime.  Per eventuali altre domande sulla <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica OpenXR 1,0</a>, visitare il <a href="https://community.khronos.org/c/openxr" target="_blank">Forum Khronos OpenXR</a> o il <a href="https://khr.io/slack" target="_blank">canale Slack #openxr</a>.

>[!NOTE]
>Si sono verificati problemi noti nel runtime corrente di Windows mixed OpenXR con app x86.  Al momento, è necessario compilare app desktop OpenXR per x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>App OpenXR che non avvia la realtà mista di Windows

Se l'app OpenXR non avvia la realtà mista di Windows quando viene eseguita, il runtime di OpenXR per la realtà mista di Windows non può essere impostato come runtime attivo.  Seguire le istruzioni per iniziare a usare [OpenXR per le cuffie con la realtà mista di Windows](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) per rendere attiva la fase di esecuzione.

È anche possibile eseguire il [strumenti di sviluppo di OpenXR per la realtà mista di Windows](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) per la risoluzione di altri problemi in merito allo stato del runtime di OpenXR per la realtà mista di Windows nel sistema.