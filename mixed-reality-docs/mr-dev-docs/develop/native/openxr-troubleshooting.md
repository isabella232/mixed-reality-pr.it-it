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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="7458c-104">Risoluzione dei problemi di OpenXR</span><span class="sxs-lookup"><span data-stu-id="7458c-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="7458c-105">Di seguito sono riportati alcuni suggerimenti per la risoluzione dei problemi durante lo sviluppo di un'app OpenXR con la realtà mista di Windows OpenXR Runtime.</span><span class="sxs-lookup"><span data-stu-id="7458c-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="7458c-106">Per eventuali altre domande sulla <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica OpenXR 1,0</a>, visitare il <a href="https://community.khronos.org/c/openxr" target="_blank">Forum Khronos OpenXR</a> o il <a href="https://khr.io/slack" target="_blank">canale Slack #openxr</a>.</span><span class="sxs-lookup"><span data-stu-id="7458c-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="7458c-107">Si sono verificati problemi noti nel runtime corrente di Windows mixed OpenXR con app x86.</span><span class="sxs-lookup"><span data-stu-id="7458c-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="7458c-108">Al momento, è necessario compilare app desktop OpenXR per x64.</span><span class="sxs-lookup"><span data-stu-id="7458c-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="7458c-109">App OpenXR che non avvia la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="7458c-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="7458c-110">Se l'app OpenXR non avvia la realtà mista di Windows quando viene eseguita, il runtime di OpenXR per la realtà mista di Windows non può essere impostato come runtime attivo.</span><span class="sxs-lookup"><span data-stu-id="7458c-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="7458c-111">Per risolvere il problema, seguire le istruzioni per iniziare a usare [OpenXR per le cuffie di realtà miste di Windows](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) .</span><span class="sxs-lookup"><span data-stu-id="7458c-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="7458c-112">È anche possibile eseguire il [strumenti di sviluppo OpenXR per la realtà mista di Windows](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) per ottenere informazioni sulla risoluzione dei problemi sullo stato del runtime di Windows Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="7458c-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>