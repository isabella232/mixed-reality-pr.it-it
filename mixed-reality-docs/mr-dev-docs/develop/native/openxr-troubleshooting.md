---
title: Risoluzione dei problemi di OpenXR
description: Risolvere i problemi delle applicazioni OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware, risoluzione dei problemi
ms.openlocfilehash: ddfe548d689d84576ad0ac06bda46d7c2757859c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612935"
---
# <a name="openxr-troubleshooting"></a>Risoluzione dei problemi di OpenXR

Di seguito sono riportati alcuni suggerimenti per la risoluzione dei problemi durante lo sviluppo di un'app OpenXR con la realtà mista di Windows OpenXR Runtime.  Per eventuali altre domande sulla <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica OpenXR 1,0</a>, visitare il <a href="https://community.khronos.org/c/openxr" target="_blank">Forum Khronos OpenXR</a> o il <a href="https://khr.io/slack" target="_blank">canale Slack #openxr</a>.

>[!NOTE]
>Si sono verificati problemi noti nel runtime corrente di Windows mixed OpenXR con app x86.  Al momento, è necessario compilare app desktop OpenXR per x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>App OpenXR che non avvia la realtà mista di Windows

Se l'app OpenXR non avvia la realtà mista di Windows quando viene eseguita, il runtime di OpenXR per la realtà mista di Windows non può essere impostato come runtime attivo. Per risolvere il problema, seguire le istruzioni per iniziare a usare [OpenXR per le cuffie di realtà miste di Windows](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) .

È anche possibile eseguire il [strumenti di sviluppo OpenXR per la realtà mista di Windows](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) per ottenere informazioni sulla risoluzione dei problemi sullo stato del runtime di Windows Mixed Reality OpenXR.