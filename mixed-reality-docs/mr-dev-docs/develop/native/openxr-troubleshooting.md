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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="e5614-104">Risoluzione dei problemi di OpenXR</span><span class="sxs-lookup"><span data-stu-id="e5614-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="e5614-105">Di seguito sono riportati alcuni suggerimenti per la risoluzione dei problemi durante lo sviluppo di un'app OpenXR con la realtà mista di Windows OpenXR Runtime.</span><span class="sxs-lookup"><span data-stu-id="e5614-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="e5614-106">Per eventuali altre domande sulla <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica OpenXR 1,0</a>, visitare il <a href="https://community.khronos.org/c/openxr" target="_blank">Forum Khronos OpenXR</a> o il <a href="https://khr.io/slack" target="_blank">canale Slack #openxr</a>.</span><span class="sxs-lookup"><span data-stu-id="e5614-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="e5614-107">Si sono verificati problemi noti nel runtime corrente di Windows mixed OpenXR con app x86.</span><span class="sxs-lookup"><span data-stu-id="e5614-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="e5614-108">Al momento, è necessario compilare app desktop OpenXR per x64.</span><span class="sxs-lookup"><span data-stu-id="e5614-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="e5614-109">App OpenXR che non avvia la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="e5614-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="e5614-110">Se l'app OpenXR non avvia la realtà mista di Windows quando viene eseguita, il runtime di OpenXR per la realtà mista di Windows non può essere impostato come runtime attivo.</span><span class="sxs-lookup"><span data-stu-id="e5614-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="e5614-111">Seguire le istruzioni per iniziare a usare [OpenXR per le cuffie con la realtà mista di Windows](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) per rendere attiva la fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e5614-111">Be sure to follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="e5614-112">È anche possibile eseguire il [strumenti di sviluppo di OpenXR per la realtà mista di Windows](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) per la risoluzione di altri problemi in merito allo stato del runtime di OpenXR per la realtà mista di Windows nel sistema.</span><span class="sxs-lookup"><span data-stu-id="e5614-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>