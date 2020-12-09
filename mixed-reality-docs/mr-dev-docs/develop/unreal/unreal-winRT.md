---
title: WinRT in Unreal
description: Panoramica del plug-in di audio spaziale per Unreal Engine.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicazione remota, realtà mista, sviluppo, Guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, WinRT, DLL
ms.openlocfilehash: f86939ee53b51fad1e31d18f810d92c3d20611f8
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926064"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="4d53d-104">WinRT in Unreal</span><span class="sxs-lookup"><span data-stu-id="4d53d-104">WinRT in Unreal</span></span>

<span data-ttu-id="4d53d-105">Nel corso dello sviluppo di HoloLens potrebbe essere necessario scrivere una funzionalità usando WinRT.</span><span class="sxs-lookup"><span data-stu-id="4d53d-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="4d53d-106">Se ad esempio si apre una finestra di dialogo di file in un'applicazione HoloLens, è necessario FileSavePicker nel file di intestazione WinRT/Windows. storage. Pickers. h.</span><span class="sxs-lookup"><span data-stu-id="4d53d-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="4d53d-107">WinRT è supportato nel sistema di compilazione Unreal dalla versione 4,26 e successive.</span><span class="sxs-lookup"><span data-stu-id="4d53d-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="4d53d-108">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="4d53d-108">Next Development Checkpoint</span></span>

<span data-ttu-id="4d53d-109">Se si sta seguendo il percorso di sviluppo non reale, si sta esaminando le funzionalità della piattaforma di realtà mista e le API.</span><span class="sxs-lookup"><span data-stu-id="4d53d-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="4d53d-110">Da qui è possibile passare a qualsiasi [argomento](unreal-development-overview.md#3-platform-capabilities-and-apis) o passare direttamente alla distribuzione dell'app in un dispositivo o in un emulatore.</span><span class="sxs-lookup"><span data-stu-id="4d53d-110">From here, you can continue to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4d53d-111">Distribuzione nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="4d53d-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="4d53d-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4d53d-112">See also</span></span>
* [<span data-ttu-id="4d53d-113">API C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="4d53d-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="4d53d-114">Classe FileSavePicker</span><span class="sxs-lookup"><span data-stu-id="4d53d-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="4d53d-115">Librerie di terze parti non reali</span><span class="sxs-lookup"><span data-stu-id="4d53d-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
